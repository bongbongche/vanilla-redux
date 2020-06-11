# Learning vanilla redux

- redux.dispatch() is communication with redux reducer

- redux.subscribe detect changing

- never, ever never, ever ever, never mutate state  
  instead of that, make a new array.  
  for example,  
   _Bad_ state.push(action.text)  
   _Good_ [...state, {text: action.text}]
