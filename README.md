# VALUE ITERATION ALGORITHM

## AIM

Implement value iteration algorithm to find optimal policy for the altered frozen lake environment.

## PROBLEM STATEMENT
Make alterations in the default frozen lake environment like changing the starting state, goal state and holes in the environment. Further find optimal policy using value iteration.

## VALUE ITERATION ALGORITHM
#### Step 1:
Import required libraries for the program.

#### Step 2:
Load the frozen lake environment and make changes.

#### Step 3:
Define the value iteration function.

#### Step 4:
Run the function and display the result

## VALUE ITERATION FUNCTION
### Name: SANTHOSH KUMAR R
### Register Number: 212223240153
```
def value_iteration(P, gamma=0.99, theta=1e-10):

    V = np.zeros(len(P), dtype=np.float64)

    while True:

        Q = np.zeros(
            (len(P), len(P[0])),
            dtype=np.float64
        )

        for s in range(len(P)):

            for a in range(len(P[s])):

                for prob, next_state, reward, done in P[s][a]:

                    Q[s][a] += prob * (
                        reward +
                        gamma * V[next_state] * (not done)
                    )

        new_V = np.max(Q, axis=1)

        if np.max(np.abs(V - new_V)) < theta:
            V = new_V
            break

        V = new_V

    pi = lambda s: np.argmax(Q[s])

    return V, pi

```

## OUTPUT:

#### OPTIMAL POLICY
<img width="408" height="122" alt="image" src="https://github.com/user-attachments/assets/4f36bf6d-7fa6-4f86-9e70-3d191ab61b29" />


#### SUCCESS RATE OF OPTIMAL POLICY
<img width="862" height="391" alt="image" src="https://github.com/user-attachments/assets/3e07618b-02a5-44e9-86f2-c384239a377e" />


#### STATE VALUE FUNCTION
<img width="613" height="265" alt="image" src="https://github.com/user-attachments/assets/707c0a35-90c2-4bbf-8019-28808774be60" />


## RESULT:

Therefore, value iteration algorithm to find optimal policy for the altered frozen lake environment is successfully implemented.
