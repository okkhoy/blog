# My Musings with LaTeX 

I am still learning LaTeX, even after using it for over 5 years now.
In this page, I will record those small things that matter!

## Take care of the small things!

### Enumeration

Native LaTeX supports enumeration and itemization, which suffices for most.
In times when we have to customize enumerations or items there are three packages (that I am aware of!).
- [Enumerate](https://ctan.org/pkg/enumerate)
- [Enumitem](https://ctan.org/pkg/enumitem)
- [Paralist](https://ctan.org/pkg/paralist)

However, there are some shared symbols between these packages that, sometimes, make it difficult to get what we want.
What I recently learned is that many of these issues can be solved by ordering the package "imports" the right way.
Importing in proper order enables the TeX engine to overload the symbols in the most sensible way.

The current order of import I follow on a [Beamer](https://ctan.org/pkg/beamer) document is as follows.
1. The oldest of the packages `paralist` goes first
2. Followed by `enumerate`
3. `enumitem` goes last.
    - Include the `shortlabels` flag for `enumitem` to enable using things like `[a)]`, `[(i)]` etc., in the item labels.
