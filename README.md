# Cat and Mouse Problem

## Problem Statement

You are given two cats and a mouse. The cats and the mouse are positioned on a straight line. You need to determine which cat catches the mouse first, or if they reach the mouse at the same time, in which case the mouse escapes.

- If Cat A catches the mouse first, print `Cat A`.
- If Cat B catches the mouse first, print `Cat B`.
- If both cats reach the mouse at the same time, print `Mouse C`.

### Function Signature

```csharp
static string catAndMouse(int x, int y, int z)
```
## Parameters
`int x`: Cat A's position.
`int y`: Cat B's position.
`int z`: Mouse's position.
*Returns*
string: Either Cat A, Cat B, or Mouse C.
## Input Format
The first line contains a single integer q, denoting the number of queries.
Each of the q subsequent lines contains three space-separated integers describing the respective values of x (cat A's location), y (cat B's location), and z (mouse's location).

Constraints
`1 ≤ q ≤ 100`
`1 ≤ x, y, z ≤ 100`
## Example
Sample Input
``` plaintext
2
1 2 3
1 3 2
Sample Output
``` plaintext
Cat B
Mouse C
```
## Explanation
Query 0: The positions of the cats and mouse are shown below:

`Cat A` is at position 1
`Cat B `is at position 2
`Mouse` is at position 3
Cat B will catch the mouse first, so the output is Cat B.

Query 1: The positions of the cats and mouse are shown below:

`Cat A` is at position 1
`Cat B `is at position 3
`Mouse` is at position 2
Both cats reach the mouse at the same time, so the output is Mouse C.

## Solution
*Approach*
Calculate the absolute distance of Cat A from the mouse.
Calculate the absolute distance of Cat B from the mouse.
Compare the distances:
If `Cat A's` distance is less than Cat B's distance, return Cat A.
If `Cat B's` distance is less than Cat A's distance, return Cat B.
If both distances are equal, return Mouse C.
## Implementation
``` csharp
using System;

class Solution {

    // Complete the catAndMouse function below.
    static string catAndMouse(int x, int y, int z) {
        // Calculate the distances of Cat A and Cat B from the mouse
        int distanceA = Math.Abs(z - x);
        int distanceB = Math.Abs(z - y);
        
        // Compare distances to determine the result
        if (distanceA < distanceB) {
            return "Cat A";
        } else if (distanceB < distanceA) {
            return "Cat B";
        } else {
            return "Mouse C";
        }
    }

    static void Main(string[] args) {
        int q = Convert.ToInt32(Console.ReadLine());

        for (int qItr = 0; qItr < q; qItr++) {
            string[] xyz = Console.ReadLine().Split(' ');

            int x = Convert.ToInt32(xyz[0]);
            int y = Convert.ToInt32(xyz[1]);
            int z = Convert.ToInt32(xyz[2]);

            string result = catAndMouse(x, y, z);

            Console.WriteLine(result);
        }
    }
}
```
