# Stanのドリル

Timed math drills for Japanese elementary school, pitched at the entrance exams of selective private middle schools (中学受験). Pick a grade, get 15 freshly generated questions, and receive both an accuracy score and a speed grade when you finish.

Available in **日本語 / 中文 / English**.

## What it does

- **Six grade levels.** Each level draws only on material taught up to that year of the Japanese curriculum (学習指導要領) — grade 4 will never ask about ratios, grade 6 will.
- **Questions are generated, not stored.** 96 generators randomise their own numbers, so the same set essentially never comes round twice.
- **Applied problems in the back half.** Grades 4–6 finish with 3–5 multi-step problems, mirroring the structure of a real exam paper: 計算・小問 first, 応用問題 last. They are marked with a vermilion tag and set off on the answer rail by a divider.
- **Two results, reported separately.** Accuracy out of 15, and time against a target calculated from the workload of that particular set. Speed grades: **A** within target, **B** within 120%, **C** within 150%, **D** beyond.
- **Marked answers.** Every question is reviewed afterwards with ○ / ×, the correct answer, and a worked explanation.
- Past attempts are kept in the browser; light and dark themes; works on phones.

## Topics by grade

| Grade | Coverage |
|---|---|
| 1 | Adding and subtracting, order problems, clocks, number patterns, listing |
| 2 | Times tables, units, elapsed time, cycles, trees and gaps, first fractions |
| 3 | Division with remainders, first decimals and fractions, sum-and-difference, circles, tables |
| 4 | Rounding, decimal × ÷, composite areas, angles, averages, sharing in parts **+ applied** |
| 5 | Factors and multiples, percentages, speed, areas, volume, surplus-and-shortage **+ applied** |
| 6 | Fraction × ÷, circles and solids, ratio, counting, travel and work problems **+ applied** |

Applied problems include averages combined with sum-and-difference, paths cut through a field, periodic counting, exchange problems, double percentages, harmonic average speed, remainder conditions, salt-solution mixing, travel with ratios, catching-up, and adjacent arrangements.

## Running it

It is one self-contained HTML file with no dependencies, no build step and no network calls. Open `index.html` in a browser and it works — including offline.

To serve it locally instead:

```bash
python3 -m http.server 8731
```

## Deploying

Any static host will do. The quickest route with no tooling is [Vercel Drop](https://vercel.com/drop): drag the folder onto the page and it deploys as-is. Vercel CLI, Netlify, GitHub Pages and Cloudflare Pages all work too — there is nothing to build.

## How answers are checked

Fill-in answers are parsed rather than string-matched, so full-width digits (１２), fractions (`3/4`), mixed numbers (`1 1/2` or `1と1/2`) and stray spaces are all accepted. Values are compared numerically with a relative tolerance.

## Correctness

The question bank is verified by a harness that runs in the browser console against the loaded page:

- Every generator is run hundreds of times in all three languages and checked for malformed text, duplicate multiple-choice options, unreduced fractions, non-terminating decimals, and answers that fail to round-trip through the answer parser.
- Full papers are built and auto-answered with the stated answers to confirm the marking logic agrees, and to confirm the paper structure (15 questions, applied problems contiguous at the end, none below grade 4).
- The applied problems are additionally re-derived by independent means rather than by reusing the generating formula — filling a grid cell by cell for the path-cutting area, enumerating permutations for the adjacency count, walking the integers for the remainder conditions, checking that both travellers cover the same distance in the catching-up problem, and so on.

## 中文说明

这是一个面向日本小学 1〜6 年级的数学练习网页，难度对标难关私立中学的入学考试。选好年级后随机生成 15 道题，做完立刻给出正确率和用时两项结果，并按用时给出 A/B/C/D 速度评级（目标用时根据本次题量估算）。4〜6 年级会在卷子后半段混入 3〜5 道需要多步推理的综合题。界面和题目支持日语、中文、英文三种语言。

整个应用是单个 HTML 文件，无依赖、无构建、不联网，双击即可打开使用。
