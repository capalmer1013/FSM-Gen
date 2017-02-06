# FSM-Gen

A language to generate FSMs in Python.

---
## Relevant Things to Read
[Modeling Language](https://en.wikipedia.org/wiki/Modeling_language)
[Behavior Tree](https://en.wikipedia.org/wiki/Behavior_tree)
---
## Possible Features
- Graphical interface to generate fsm code

---
## Language example

```
state A;
state B;
state C;
state D;

cond J;
cond K;
cond L;

START -> A;
A -> B;
B -> C;
C -> A;
A -> D;
D -> END;  // optional END node

[A, B] = (J && K)
[B, C] = (L)
[C, A] = (J ^ K)
[A, D] = (~L || K)
[D, END] = (J || K || L)

```

*maybe add a way to do state execution in language. Or just leave it as a modeling language.

```python
class sampleState:
	stateMachine = {
		0: A,
		1: B,
		2: C,
		3: D,
		4: END
	}
	def __init__(self):
		self.J = None
		self.K = None
		self.L = None
	
	def ExecuteStateMachine(self):
		nextState = 0
		while nextState != -1:
			nextState = stateMachine[nextState](self)  # This might not work
	
	def A(self):
		# do something
		if <condition>:
			return 1
		return 3

	def B(self):
		# do something
		return 2

	def C(self):
		# do something
		return 0

	def D(self):
		# do something
		return 4

	def END(self):
		return -1
```
