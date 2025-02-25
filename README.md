# Simplest-Stream-Files

package simplestreamandfileexample;
import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.util.List;
import java.util.stream.Collectors;
public class SimpleStreamAndFileExample {
public static void main(String[] args) {

String inputFilePath = &quot;input_names.txt&quot;;
String outputFilePath = &quot;output_uppercase.txt&quot;;
try {
List&lt;String&gt; names = readNamesFromFile(inputFilePath);

List&lt;String&gt; uppercaseNames = names.stream().map(String::toUpperCase).collect(Collectors.toList());

writeUppercaseNamesToFile(outputFilePath, uppercaseNames);
System.out.println(&quot;Uppercase names written to &quot; + outputFilePath);
} catch (IOException e) {

e.printStackTrace();
}
}
private static List&lt;String&gt; readNamesFromFile(String filePath) throws IOException {
try (BufferedReader reader = new BufferedReader(new FileReader(filePath))) {
return reader.lines().collect(Collectors.toList());
}
}
private static void writeUppercaseNamesToFile(String filePath, List&lt;String&gt;
uppercaseNames) throws IOException {
try (BufferedWriter writer = new BufferedWriter(new FileWriter(filePath))) {
for (String name : uppercaseNames) {
writer.write(name);
writer.newLine();
}
}
}
}

Output:

ALICE
BOB
CHARLIE
DAVID
EVE
