# Perface
## CHANGES IN THE THIRD EDITION

The changes introduced in the third edition of Engineering a Com- piler (EaC3e) arise from two principal sources: changes in the way that programming-language translation technology is used and changes in the technical backgrounds of our students. These two driving forces have led to continual revision in the way that we teach compiler construction. This third edition captures those classroom-tested changes.

EaC3e reorganizes the material, discarding some topics from prior editions and introducing some topics that are new—at least in this book. EaC2e included major changes to the material on optimization (Chapters 8, 9, and 10); those chapters are largely intact from the second edition. For EaC3e, we have made changes throughout the book, with a particular focus on re- organization and revision in the middle of the book: Chapters 4 through 7. The widespread use of just-in-time (JIT) compilers prompted us to add a chapter to introduce these techniques. In terms of specific content changes:

- The chapter on intermediate representations now appears as Chapter 4, before syntax-driven translation. Students should be familiar with that material before they read about syntax-driven translation.
    
- The material on attribute grammars that appeared in Chapter 4 of the first two editions is gone. Attribute grammars are still an interesting topic, but it is clear that ad-hoc translation is the dominant paradigm for translation in a compiler’s front end.
    
- Chapter 5 now provides a deeper coverage of both the mechanism of syntax-driven translation and its use. Several translation-related topics that were spread between Chapters 4, 6, and 7 have been pulled into this new chapter.
    
- Chapter 7 has a new organization and structure, based on extensive in- class experimentation.
> Earlier editions called Best’s algorithm the “bottom-up local” algorithm.
- Chapter 13 now focuses on two allocators: a local allocator based on Best’s algorithm and a global allocator based on the work of Chaitin and Briggs. The Advanced Topics section of Chapter 13 explores modifica- tions of the basic Chaitin-Briggs scheme that produce techniques such as linear scan allocators, SSA-based allocators, and iterative coalescing allocators.
    
- Chapter 14 provides an overview of runtime optimization or JIT- compilation. JIT compilers have become ubiquitous. Students should understand how JIT compilers work and how they relate to classic ahead-of-time compilers.

Our goal continues to be a text and a course that expose students to critical issues in modern compilers and provide them with the background to tackle those problems.

We usually omit Chapters 9 and 10 in the undergraduate course. Chapter 14 elicits, in our experience, more student interest.

## ORGANIZATION

EaC3e divides the material into four roughly equal pieces:

■ The first section, Chapters 2 and 3, covers the design of a compiler’s front end and the algorithms that go into tools that automate front-end construction. In teaching the algorithms to derive scanners from regular expressions and parsers from context-free grammars, the text introduces several key concepts, including the notion of a fixed-point algorithm.

■ The second section, Chapters 4 through 7, explores the mapping of source code into the compiler’s intermediate form. These chapters ex- amine the kinds of code that the front end can generate for the optimizer and the back end.

> We usually omit Chapters 9 and 10 in the undergraduate course. Chapter 14 elicits, in our experience, more student interest.

■ The third section, Chapters 8, 9, 10, and 14, presents an overview of code optimization. Chapter 8 provides a broad look at the kinds of op- timization that compilers perform. Chapters 9 and 10 dive more deeply into data-flow analysis and scalar optimization. Chapter 14 fits themati- cally into this section; it assumes knowledge of the material in the fourth section.

■ The fourth section, Chapters 11 through 13, focuses on the major algo- rithms found in a compiler’s back end: instruction selection, instruction scheduling, and register allocation. In the third edition, we have revised the material on register allocation so that it focuses on fewer ideas and covers them at greater depth. The new chapter provides students with a solid basis for understanding most of the modern allocation algo- rithms.

Our undergraduate course takes a largely linear walk through this material. We often omit Chapters 9 and 10 due to a lack of time. The material in Chapter 14 was developed in response to questions from students in the course.

## APPROACH

Compiler construction is an exercise in engineering design. The compiler writer must choose a path through a design space that is filled with di- verse alternatives, each with distinct costs, advantages, and complexity. Each decision has an impact on the resulting compiler. The quality of the end product depends on informed decisions at each step along the way.

Thus, there is no single right answer for many of the design decisions in a compiler. Even within “well-understood” and “solved” problems, nuances in design and implementation have an impact on both the behavior of the compiler and the quality of the code that it produces. Many considerations play into each decision. As an example, the choice of an intermediate repre- sentation for the compiler has a profound impact on the rest of the compiler, from time and space requirements through the ease with which different al- gorithms can be applied. The decision, however, is often given short shrift. Chapter 4 examines the space of intermediate representations and some of the issues that should be considered in selecting one. We raise the issue again at several points in the book—both directly in the text and indirectly in the exercises.

EaC3e explores the compiler construction design space and conveys both the depth of problems and the breadth of the possible solutions. It presents some of the ways that problems in compilation have been solved, along with the constraints that made those solutions attractive. Compiler writers need to understand both the parameters of the problems and their solutions. They must recognize that a solution to one problem can affect both the opportu- nities and constraints that appear in other parts of the compiler. Only then can they make informed and intelligent design choices.


## PHILOSOPHY

This text exposes our philosophy for building compilers, developed during more than forty years each of research, teaching, and practice. For example, intermediate representations should expose those details that matter in the final code; this belief leads to a bias toward low-level representations. Val- ues should reside in registers until the allocator discovers that it cannot keep them there; this practice leads to compilers that operate in terms of virtual registers and that only store values to memory when it cannot be avoided. This approach also increases the importance of effective algorithms in the compiler’s back end. Every compiler should include optimization; it simpli- fies the rest of the compiler. Our experiences over the years have informed the selection of material and its presentation.

## A WORD ABOUT PROGRAMMING EXERCISES

A class in compiler construction offers the opportunity to explore complex problems in the context of a concrete application—one whose basic func- tions are well understood by any student with the background for a compiler construction course. In most versions of this course, the programming exer- cises play a large role.

We have taught this class in versions where the students build a simple com- piler from start to finish—beginning with a generated scanner and parser and ending with a code generator for some simplified RISC instruction set. We have taught this class in versions where the students write programs that address well-contained individual problems, such as register allocation or instruction scheduling. The choice of programming exercises depends heavily on the role that the course plays in the surrounding curriculum.

In some schools, the compiler course serves as a capstone course for seniors, tying together concepts from many other courses in a large, practical, design and implementation project. Students in such a class might write a complete compiler for a simple language or modify an open-source compiler to add support for a new language feature or a new architectural feature. This ver- sion of the class might present the material in a linear order that closely follows the text’s organization.

In some schools, that capstone experience occurs in other courses or in other ways. In this situation, the teacher might focus the programming exercises more narrowly on algorithms and their implementations, using labs such as a local register allocator or a tree-height rebalancing pass. This version of the course might skip around in the text and adjust the order of presenta- tion to meet the needs of the labs. We have found that students entering the course understand assembly-language programming, so they have no prob- lem understanding how a scheduler or a register allocator should work.

In either scenario, the course should make connections to other classes in the undergraduate curriculum. The course has obvious ties to computer or- ganization, assembly-language programming, operating systems, computer architecture, algorithms, and formal languages. Less obvious connections abound. The material in Chapter 7 on character copying raises performance issues that are critical in protocol-stack implementation. The material in Chapter 2 has applications that range from URL-filtering through specify- ing rules for firewalls and routers. And, of course, Best’s algorithm from Chapter 13 is an earlier version of Belady’s offline page replacement algo- rithm, MIN.

## ADDITIONAL MATERIALS

Additional resources are available to help you adapt the material pre- sented in EaC3e to your course. These include a complete set of slides from the authors’ version of the course at Rice University and a set of solutions to the exercises. Visit https://educate.elsevier.com/book/details/ 
9780128154120 for more information.

## ACKNOWLEDGMENTS

Many people were involved in the preparation of this third edition of Engi- neering a Compiler. People throughout the community have gently pointed out inconsistencies, typographical problems, and errors. We are grateful to each of them.

Teaching is often its own reward. Two colleagues of ours from the class- room, Zoran Budimlic ́ and Michael Burke, deserve special thanks. Zoran is a genius at thinking about how to abstract a problem. Michael has deep insights into the theory behind both the front-end section of the book and the optimization section. Each of them has influenced the way that we think about some of this material.

The production team at Elsevier, specifically Beth LoGiudice, Steve Merken, and Manchu Mohan, played a critical role in the conversion of a rough manuscript into its final form. All of these people improved this volume in significant ways with their insights and their help. Aaron Keen, Michael Lam, and other reviewers provided us with valuable and timely feedback on Chapter 14.

Finally, many people have provided us with intellectual and emotional sup- port over the last five years. First and foremost, our families and our col- leagues at Rice have encouraged us at every step of the way. Christine and Carolyn, in particular, tolerated myriad long discussions on topics in compiler construction. Steve Merken guided this edition from its inception through its publication with enthusiasm, extreme patience, and good humor. To all these people go our heartfelt thanks.
