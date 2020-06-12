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

# Learning react-redux

- To connect store to component, use connect()  
  For example, connect(mapStateToProps)(component)  
  Now component connects with store.  
  mapStateToProps is function. It takes two arguments  
  One is state, Two is ownProps  
  - state is state from redux  
    if mapStateToProps return { state }, component can get state as a prop
  - ownProps show props that component has.
