Parent: [[+ bash]]

- the shell's parser performs transformations on commands before executing them
- the order of these expansions it performs is:
  1.  [[brace expansion]]
  2.  [[tilde expansion]]
  3.  [[parameter expansion]], variable, and [[arithmetic expansion]] and [[command substitution]] (done in a left-to-right fashion)
  4.  [[word splitting]]
  5.  [[glob]] expansion
