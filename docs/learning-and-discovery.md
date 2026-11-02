# Learning and discovery in v0.5.0

The website and installed Android/Windows apps share these features. Local practice, puzzle guides and algorithm references are bundled; account services, human matches and streamed videos need a connection.

## Choose a puzzle, then a purpose

Learn separates **Puzzle guides**, **Algorithms**, **Courses**, **Methods & skills**, and **Playground**. Algorithm filters separate puzzle, method, case set, level and search. Courses have their own view and progress. A continuation card opens an unfinished course.

There are 18 learning paths: the 17 WCA events and Mirror blocks. The 28 courses contain 101 lessons. Existing 3×3 interactive lessons still require the knowledge answer and a manually solved case. New puzzle courses use concept checks with self-directed physical drills; completion of those checks is not presented as a verified solve.

The timer supports 15 timed events: 2×2 through 7×7, one-handed, 3/4/5 blindfolded, Pyraminx, Skewb, Megaminx, Square-1 and Clock. FMC and multi-blind have learning paths, but CubeHub does not treat ordinary elapsed-time statistics as their official scores. Mirror algorithms use a standard 3×3 topology preview.

## Algorithm coverage and notation

The library contains 2,825 algorithm and technique references, including 975 added source references. New sets cover 2×2 Ortega/CLL/EG, 4×4 parity, 5×5 reduction cases, Square-1, Megaminx, Pyraminx and Skewb. Named sets reflect the formulas available in their source pages; the library is not a claim to contain every possible solution or variation. Empty source groups are not filled with invented algorithms. Duplicate source names with distinct formulas are labeled as variations.

Move sequences and case labels reference [SpeedCubeDB](https://www.speedcubedb.com/); links to individual cases are retained in each record. CubeHub's explanations, course text and interface are written separately. Source illustrations, comments, ratings and account data are not copied. The original 3×3 catalog retains its [Cubedex attribution](https://github.com/poliva/cubedex/tree/8a8b5b99ef69386d874bbb9662702efff165c1cd).

Interactive references use the matching puzzle and an inverse-case preview. Square-1 tuple spacing is normalized without changing moves. Source-specific notation that the local model cannot interpret is labeled **Source notation**, with a source link instead of an incorrect animation. This includes Sarah-style Skewb references and some compound 4×4 references. Each reference retains its source link; the catalog counts the entries actually available rather than promising every possible algorithm.

The generator is [cubing.js](https://js.cubing.net/cubing/scramble/), with event-specific scramble methods. Scramble moves can be marked as you follow them, copied, and checked against a 2D net or 3D view. Requests are protected against stale responses when changing events. Official competitions supply their own scrambles and use the [current WCA regulations](https://www.worldcubeassociation.org/regulations/).

## A method-based practice bot

3×3 choices are **CFOP**, **colour-neutral CFOP**, and **beginner layer by layer**. The CFOP planner solves a cross, extracts/recognizes/inserts F2L cases, and finishes with OLL/PLL. The beginner planner completes corners, middle edges and separate last-layer steps. The 2×2 bot uses a layer and corner orientation/permutation.

Every plan is checked against the cube state. Failures ask for another preparation attempt rather than silently presenting an inverse scramble as a human method. The worker keeps planning off the UI thread. Race and replay rhythm includes stage pauses. The race shows the current method step and no total move count. These remain simulated practice opponents with no competitive rating.

## Watch with a purpose

Videos are separated into **Learning**, **Solves & competition**, **Fun & challenges**, **News & discussion**, and **Cuber stories**, with puzzle, method, topic and bookmark filters. The 94 entries include 44 additions whose titles, creators and embedding availability were checked with YouTube's public oEmbed endpoint on November 2, 2026.

Older raw solve clips are classified as solve footage, rather than tutorials. News is a curated archive, not a live feed; dated claims belong in their publication context. Videos are streamed from YouTube, not downloaded or rehosted. Bookmarks and notes remain part of practice sync. Examples include [WCA 2025 3×3 finals](https://www.youtube.com/watch?v=xpmcqOZp5PQ), [J Perm's Megaminx tutorial](https://www.youtube.com/watch?v=oVRooYDvRqg), and [Tymon Kolasiński's Q&A](https://www.youtube.com/watch?v=KXymzWEtEL4).

## A broader built-in Coach

Smart Coach combines event-specific personal analysis with a larger cubing knowledge index, method/course lookup, notation explanations, algorithm references and contextual follow-ups. It can distinguish puzzle notation and route current-record questions to official results instead of inventing live facts. This is deterministic software, not general-purpose language-model understanding.

The existing access policy remains five answered questions per UTC day for free accounts and unlimited daily questions for AI Premium. Clarifications do not spend allowance. Administrators control manual Premium grants. No external model calls or model fees are required.

The timer history now starts with the ten most recent solves, with **Show 10 more** and **Recent 10 only** controls. Export still includes the session's saved records.

Offline timer suggestions use local solves and recorded manual splits. They do not request an unavailable online review or show a connection toast. Smart Cube recording needs the account service; local cube viewing remains available.
