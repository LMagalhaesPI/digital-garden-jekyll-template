---
title: Conventional commits!! What is it and how to use it!
---

Conventional commits are conventions used on commit messages. The goal is to have a set of rules for creating an explicit commit history. It will make it easier to use automated tools on top of that. With this approach, it's easier to read the branch history and manage the relation between commits and tasks or stories.

The structure to be followed in the commits messages:


```
_type(_task_number): _description
```

The type can be any of the following:

✔️ fix: fixes a bug. <br/>
✔️ feat: adds new functionality. <br/>
✔️ docs: adds or improves documentation. <br/>
✔️ test: adds tests. <br/>
✔️ perf: improves performance, without functional changes. <br/>
✔️ chore: a catch-all type for any other commits. For instance, if you're implementing a single feature and it makes sense to divide the work into multiple commits, you should mark one commit as feat and the rest as chore. <br/>
✔️ refactor: refactoring code <br/>

Example:
```
feat(TASK-123): Add this new great feature!
```

👉 To ensure that we have just one commit to the dev or main branch per task we will use squash or commit amend.

👉 We can use the ! (exclamation mark) to signalize breaking changes.

This is a great tool to improve the communication inside the team and even between teams in cross-team projects. As the following topics:
[[Which communication channels to use and when❓❓]]
