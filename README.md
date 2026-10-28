# ExpNo:10 Implementation of Classical Planning Algorithm
## NAME: Viswapriya S
## REG.NO: 212225230311
# Algorithm or Steps Involved:
<ol>
  <li>Define the initial state</li>
  <li>Define the goal state</li>
  <li>Define the actions</li>
  <li>Find a <b>plan</b> to reach the goal state</li>
  <li>Print the plan</li>
</ol>

# Example - 1
```
initial_state = {'A': 'Table', 'B': 'Table'}
goal_state = {'A': 'B', 'B': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_Table': {'precondition': {'A': 'Table', 'B': 'B'}, 'effect': {'B': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B']
```
# Example - 2
```
initial_state = {'A': 'Table', 'B': 'Table', 'C': 'Table'}
goal_state = {'A': 'B', 'B': 'C', 'C': 'Table'}

actions = {
    'move_A_to_B': {'precondition': {'A': 'Table', 'B': 'Table'}, 'effect': {'A': 'B'}},
    'move_B_to_C': {'precondition': {'A': 'B', 'B': 'Table', 'C': 'Table'}, 'effect': {'B': 'C'}},
    'move_C_to_Table': {'precondition': {'A': 'B', 'B': 'C', 'C': 'C'}, 'effect': {'C': 'Table'}}
}

plan = find_plan(initial_state, goal_state, actions)
print(plan)
```
# Output:
```
['move_A_to_B', 'move_B_to_C']
```

# Please Prepare Solution or Definition For the method find_plan(initial_state, goal_state, actions)
<h3>You Can use any of the searching Strategies for planning and executing a sequence of actions.<br> You can also look in to the Code given in the Repository.</h3>

## PROGRAM:
```
from collections import deque

def find_plan(initial_state, goal_state, actions):
    queue = deque([(initial_state, [])])
    visited = set()

    while queue:
        state, plan = queue.popleft()

        if all(state.get(k) == v for k, v in goal_state.items()):
            return plan

        key = tuple(sorted(state.items()))

        if key in visited:
            continue
        visited.add(key)

        for name, action in actions.items():
            if all(state.get(k) == v
                   for k, v in action['precondition'].items()):
                new_state = state.copy()
                new_state.update(action['effect'])
                queue.append((new_state, plan + [name]))

    return []


# Example 1
initial_state = {'A': 'Table', 'B': 'Table'}
goal_state = {'A': 'B', 'B': 'Table'}

actions = {
    'move_A_to_B': {
        'precondition': {'A': 'Table', 'B': 'Table'},
        'effect': {'A': 'B'}
    },
    'move_B_to_Table': {
        'precondition': {'A': 'Table', 'B': 'B'},
        'effect': {'B': 'Table'}
    }
}

print(find_plan(initial_state, goal_state, actions))


# Example 2
initial_state = {'A': 'Table', 'B': 'Table', 'C': 'Table'}
goal_state = {'A': 'B', 'B': 'C', 'C': 'Table'}

actions = {
    'move_A_to_B': {
        'precondition': {'A': 'Table', 'B': 'Table'},
        'effect': {'A': 'B'}
    },
    'move_B_to_C': {
        'precondition': {'A': 'B', 'B': 'Table', 'C': 'Table'},
        'effect': {'B': 'C'}
    },
    'move_C_to_Table': {
        'precondition': {'A': 'B', 'B': 'C', 'C': 'C'},
        'effect': {'C': 'Table'}
    }
}

print(find_plan(initial_state, goal_state, actions))


# Example 3
initial_state = {'A': 'Table', 'B': 'Table'}
goal_state = {'A': 'C'}

actions = {
    'move_A_to_B': {
        'precondition': {'A': 'Table', 'B': 'Table'},
        'effect': {'A': 'B'}
    }
}

print(find_plan(initial_state, goal_state, actions))
```

## OUTPUT:

<img width="1398" height="98" alt="WhatsApp Image 2026-10-21 at 9 48 59 AM" src="https://github.com/user-attachments/assets/f570fd0a-27bf-4173-817f-5298941f85fa" />

## RESULT:
Therefore,Implementation of Classical Planning Algorithm is implemetated successfully.

