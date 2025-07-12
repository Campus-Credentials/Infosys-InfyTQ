**Question 1:Meeting Rooms II**

**Solution in Python**
```java
def min_meeting_rooms(intervals_data: list[list[int]]) -> int:
    if not intervals_data:
        return 0

    # Sort intervals by start time
    intervals_data.sort(key=lambda x: x[0])

    # List to keep track of end times of meetings in rooms
    room_end_times = [intervals_data[0][1]]

    for i in range(1, len(intervals_data)):
        start, end = intervals_data[i]

        # Find a room whose meeting has ended before this one starts
        found_room = False
        for j in range(len(room_end_times)):
            if room_end_times[j] <= start:
                # Reuse this room
                room_end_times[j] = end
                found_room = True
                break
        
        if not found_room:
            # No available room, so allocate a new one
            room_end_times.append(end)

        # Keep end times sorted (like a min-heap would do)
        room_end_times.sort()

    return len(room_end_times)

# Main execution block for taking input
if __name__ == "__main__":
    N = int(input())
    intervals = []
    for _ in range(N):
        start, end = map(int, input().split())
        intervals.append([start, end])
    
    result = min_meeting_rooms(intervals)
    print(result)

```
**Solution in Java**
```java
import java.util.Arrays;
import java.util.PriorityQueue;
import java.util.Scanner;

public class MeetingRoomsII {

    public static int minMeetingRooms(int[][] intervals) {
        if (intervals == null || intervals.length == 0) {
            return 0;
        }

        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));

        PriorityQueue<Integer> roomEndTimes = new PriorityQueue<>();

        roomEndTimes.add(intervals[0][1]);

        for (int i = 1; i < intervals.length; i++) {
            int currentMeetingStart = intervals[i][0];
            
            if (!roomEndTimes.isEmpty() && currentMeetingStart >= roomEndTimes.peek()) {
                roomEndTimes.poll();
            }
            
            roomEndTimes.add(intervals[i][1]);
        }
        
        return roomEndTimes.size();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int N = Integer.parseInt(scanner.nextLine());
        int[][] intervals = new int[N][2];
        for (int i = 0; i < N; i++) {
            String[] parts = scanner.nextLine().split(" ");
            intervals[i][0] = Integer.parseInt(parts[0]);
            intervals[i][1] = Integer.parseInt(parts[1]);
        }
        
        int result = minMeetingRooms(intervals);
        System.out.println(result);
        scanner.close();
    }
}

```
