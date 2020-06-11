# Learning vanilla redux

- redux.dispatch() is communication with redux reducer

- redux.subscribe detect changing

- never, ever never, ever ever, never mutate state  
  instead of that, make a new array.  
  for example,  
   **Bad** - state.push(action.text)  
   **Good** - [...state, {text: action.text}]  
   **Good** - state.filter(toDo => toDo.id !== action.id)

- filter() returns a new array
