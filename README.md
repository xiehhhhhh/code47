# code47
package jykh;
import java.util.Stack;
import java.util.Scanner;
 
public class jykh {
    public static boolean areBracketsBalanced(String expr) {
        Stack<Character> stack = new Stack<>();

        for (char c : expr.toCharArray()) {
            if (c == '(' || c == '[' || c == '{') {
                stack.push(c);
            } else if (c == ')' || c == ']' || c == '}') {
                if (stack.isEmpty()) {
                    return false;
                }
                char lastBracket = stack.pop();
                if ((c == ')' && lastBracket != '(') ||
                        (c == ']' && lastBracket != '[') ||
                        (c == '}' && lastBracket != '{')) {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入一个包含括号的表达式：");
        String expr = scanner.nextLine();
        boolean isBalanced = areBracketsBalanced(expr);
        System.out.println("括号是否平衡？ " + (isBalanced ? "是" : "否"));
    }
}
