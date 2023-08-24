# Mountblue-Hackerrank-Solution
Unique solution in java for Misère Nim

import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.function.*;
import java.util.regex.*;
import java.util.stream.*;
import static java.util.stream.Collectors.joining;
import static java.util.stream.Collectors.toList;

class Result {

    /*
     * Complete the 'misereNim' function below.
     *
     * The function is expected to return a STRING.
     * The function accepts INTEGER_ARRAY s as parameter.
     */

    public static String misereNim(List<Integer> s) {
    // Write your code here
         int length = s.size();
        int sum = 0;
        int xorAll = 0;

        if (length == 1) {
            return s.get(0) > 1 ? "First" : "Second";
        }

        for (int i = 0; i < length; i++) {
            xorAll ^= s.get(i);
            sum += s.get(i);
        }

        if (sum == length) {
            return (sum & 1) == 1 ? "Second" : "First";
        }

        return xorAll > 0 ? "First" : "Second";

    }

}

public class Solution {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int t = Integer.parseInt(bufferedReader.readLine().trim());

        IntStream.range(0, t).forEach(tItr -> {
            try {
                int n = Integer.parseInt(bufferedReader.readLine().trim());

                List<Integer> s = Stream.of(bufferedReader.readLine().replaceAll("\\s+$", "").split(" "))
                    .map(Integer::parseInt)
                    .collect(toList());

                String result = Result.misereNim(s);

                bufferedWriter.write(result);
                bufferedWriter.newLine();
            } catch (IOException ex) {
                throw new RuntimeException(ex);
            }
        });

        bufferedReader.close();
        bufferedWriter.close();
    }
}
