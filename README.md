# 13、leetcode557. 反转字符串中的单词 III
解法一：
--  
思路：
--
    我们将输入字符串中按照空白字符串分开，然后把所有单词放到一个字符串列表中，然后我们逐一遍历每一个字符串并把反转结果连接起来。最后，我们将删除了额外空白字符的字符串返回。    
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/16 21:46
 * @descriptor
 */
public class ReverseWords_557 {
    public static String reverseWords(String s) {
        String[] strs = s.split(" ");
        StringBuilder builder = new StringBuilder();
        for (String str:strs) {
            builder.append(new StringBuilder(str).reverse().toString()+" ");
        }
        return builder.toString().trim();
    }
    public static void main(String[] args) {
        String s ="Let's take LeetCode contest";
        String s1 = reverseWords(s);
        System.out.println(s1);
    }
}
</pre>

解法二：
--  
思路：
--
    自己写一个 split 和 reverse 函数。 split 函数将字符串按照 " " （空格）为分隔符将字符串分开并返回单词列表。 reverse 函数返回每个字符串反转后的字符串。  
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/16 21:46
 * @descriptor
 */
public class ReverseWords_557 {
    public static String reverseWords(String s) {
        String[] strs = split(s);
        StringBuilder builder = new StringBuilder();
       for(String str:strs)
            builder.append(reverse(str)+" ");
        return builder.toString().trim();
    }
    public static String[] split(String s){
        StringBuilder builder = new StringBuilder();
        List<String> list = new ArrayList<>();
        for (int i = 0; i < s.length(); i++) {
            if(s.charAt(i) != ' ')
                builder.append(s.charAt(i));
            else{
                list.add(builder.toString());
                builder = new StringBuilder();
            }
        }
        list.add(builder.toString());
        return list.toArray(new String[list.size()]);
    }

    public static String reverse(String s) {
        StringBuilder builder = new StringBuilder();
        for (int i = 0; i < s.length(); i++) {
            builder.insert(0,s.charAt(i));
        }
        return builder.toString();
    }
    public static void main(String[] args) {
        String s ="Let's take LeetCode contest";
        String s1 = reverseWords2(s);
        System.out.println(s1);
    }
}
</pre>
解法三：
--     
代码： 
--
<pre>
/**
 * @author lihe
 * @date 2019/10/16 21:46
 * @descriptor
 */
public class ReverseWords_557 {
    public static String reverseWords(String s) {
        String[] strs = s.split(" ");
        StringBuilder builder = new StringBuilder();
        for (int i = 0; i < strs.length; i++) {
            char[] chars = strs[i].toCharArray();
            String ss = reverse(chars);
            if(i == strs.length-1)
                builder.append(ss);
            else
                 builder.append(ss+" ");
        }
        return builder.toString();
    }

    private static String reverse(char[] chars) {
        int l = 0;
        int r = chars.length-1;
        while(l < r) {
            char c = chars[l];
            chars[l++] = chars[r];
            chars[r--] = c;
        }
        return new String(chars);
    }
    public static void main(String[] args) {
        String s ="Let's take LeetCode contest";
        String s1 = reverseWords(s);
        System.out.println(s1);
    }
}
</pre>
