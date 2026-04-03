## Aim:
Merge Two TreeSets: One Case-Sensitive, One Case-Insensitive, Normalize Before Union

## Program:

```

import java.util.*;

public class MergeTreeSetsNormalize {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        TreeSet<String> set1 = readNormalizedSet(sc);
        TreeSet<String> set2 = readNormalizedSet(sc);

        mergeAndDisplay(set1, set2);

        sc.close();
    }

    public static TreeSet<String> readNormalizedSet(Scanner sc) {
        int n = sc.nextInt();
        sc.nextLine();
        TreeSet<String> set = new TreeSet<>();
        for (int i = 0; i < n; i++) {
            String str = sc.nextLine().trim();
            set.add(str.toLowerCase());
        }
        return set;
    }

    public static void mergeAndDisplay(TreeSet<String> set1, TreeSet<String> set2) {
        // Merge both sets
        TreeSet<String> merged = new TreeSet<>(set1);
        merged.addAll(set2);

        if (merged.isEmpty()) {
            System.out.println("No elements found.");
        } else {
            System.out.println("Merged normalized TreeSet:");
            for (String s : merged) {
                System.out.println(s);
            }
        }
    }
}

```
