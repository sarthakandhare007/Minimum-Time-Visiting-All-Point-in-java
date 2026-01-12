# Minimum-Time-Visiting-All-Point-in-java

This is **LeetCode 1266 – Minimum Time Visiting All Points**.
Let’s understand the **trick** and then I’ll give you a **clean Java solution** 👇

---

## 🔑 Key Idea (Very Important)

From point **(x1, y1)** to **(x2, y2)**:

* You can move **diagonally** → reduces both x and y by 1 in **1 second**
* Remaining distance is covered by horizontal/vertical moves

⏱️ **Minimum time needed =**

```
max( |x2 - x1| , |y2 - y1| )
```

### Why?

* Diagonal moves = `min(dx, dy)`
* Remaining moves = `|dx - dy|`
* Total = `min(dx, dy) + (|dx - dy|)` = `max(dx, dy)`

---

## 🧠 Approach

1. Start from point `points[0]`
2. For every next point:

   * Calculate `dx = |x2 - x1|`
   * Calculate `dy = |y2 - y1|`
   * Add `max(dx, dy)` to total time
3. Return total time

---

## ✅ Example 1

```
points = [[1,1], [3,4], [-1,0]]

(1,1) → (3,4) = max(2,3) = 3
(3,4) → (-1,0) = max(4,4) = 4

Total = 7
```

---

## ☕ Java Solution (Simple & Clean)

```java
class Solution {
    public int minTimeToVisitAllPoints(int[][] points) {
        int time = 0;

        for (int i = 1; i < points.length; i++) {
            int dx = Math.abs(points[i][0] - points[i - 1][0]);
            int dy = Math.abs(points[i][1] - points[i - 1][1]);
            time += Math.max(dx, dy);
        }

        return time;
    }
}
```

---

## ⏱️ Complexity

* **Time:** `O(n)`
* **Space:** `O(1)`

---

