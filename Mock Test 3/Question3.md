**Question 1: Add Two Numbers (Linked List)**

**Solution in Python**
```java
# Definition for singly-linked list node.
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def add_two_numbers(l1_str: str, l2_str: str) -> str:
    # Helper to convert list of ints to ListNode chain
    def create_linked_list(digits):
        head = None
        current = None
        for digit in digits:
            if head is None:
                head = ListNode(digit)
                current = head
            else:
                current.next = ListNode(digit)
                current = current.next
        return head

    # Helper to convert ListNode chain to list of ints
    def linked_list_to_list(node):
        result = []
        while node:
            result.append(node.val)
            node = node.next
        return result

    l1_digits = list(map(int, l1_str.split()))
    l2_digits = list(map(int, l2_str.split()))

    l1 = create_linked_list(l1_digits)
    l2 = create_linked_list(l2_digits)

    dummy_head = ListNode(0)
    current = dummy_head
    carry = 0

    while l1 or l2 or carry:
        val1 = l1.val if l1 else 0
        val2 = l2.val if l2 else 0

        total_sum = val1 + val2 + carry
        carry = total_sum // 10
        digit = total_sum % 10

        current.next = ListNode(digit)
        current = current.next

        if l1:
            l1 = l1.next
        if l2:
            l2 = l2.next

    result_list = linked_list_to_list(dummy_head.next)
    return ' '.join(map(str, result_list))

# Main execution block for taking input
if __name__ == "__main__":
    l1_str_val = input()
    l2_str_val = input()
    result = add_two_numbers(l1_str_val, l2_str_val)
    print(result)

```
**Solution in Java**
```java
import java.util.Scanner;
import java.util.Arrays;
import java.util.ArrayList;
import java.util.List;

public class AddTwoNumbersLinkedList {

    // Definition for singly-linked list. Made static nested to allow it in the same file.
    public static class ListNode {
        int val;
        ListNode next;
        ListNode(int val) { this.val = val; }
        ListNode(int val, ListNode next) { this.val = val; this.next = next; }
    }

    // Helper to convert array of ints to ListNode chain
    public static ListNode createLinkedList(int[] digits) {
        if (digits.length == 0) {
            return null;
        }
        ListNode head = new ListNode(digits[0]);
        ListNode current = head;
        for (int i = 1; i < digits.length; i++) {
            current.next = new ListNode(digits[i]);
            current = current.next;
        }
        return head;
    }

    // Helper to convert ListNode chain to space-separated string
    public static String linkedListToString(ListNode node) {
        StringBuilder sb = new StringBuilder();
        while (node != null) {
            sb.append(node.val);
            if (node.next != null) {
                sb.append(" ");
            }
            node = node.next;
        }
        return sb.toString();
    }

    public static ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummyHead = new ListNode(0);
        ListNode current = dummyHead;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int val1 = (l1 != null) ? l1.val : 0;
            int val2 = (l2 != null) ? l2.val : 0;

            int totalSum = val1 + val2 + carry;
            carry = totalSum / 10;
            int digit = totalSum % 10;

            current.next = new ListNode(digit);
            current = current.next;

            if (l1 != null) {
                l1 = l1.next;
            }
            if (l2 != null) {
                l2 = l2.next;
            }
        }

        return dummyHead.next;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Read first linked list
        String[] l1Str = scanner.nextLine().split(" ");
        int[] l1Digits = new int[l1Str.length];
        for (int i = 0; i < l1Str.length; i++) {
            l1Digits[i] = Integer.parseInt(l1Str[i]);
        }
        ListNode l1 = createLinkedList(l1Digits);

        // Read second linked list
        String[] l2Str = scanner.nextLine().split(" ");
        int[] l2Digits = new int[l2Str.length];
        for (int i = 0; i < l2Str.length; i++) {
            l2Digits[i] = Integer.parseInt(l2Str[i]);
        }
        ListNode l2 = createLinkedList(l2Digits);

        ListNode sumList = addTwoNumbers(l1, l2);
        System.out.println(linkedListToString(sumList));
        scanner.close();
    }
}

```
