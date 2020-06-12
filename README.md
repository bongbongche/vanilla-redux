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
  mapStateToProps is a function. It looks like store.getState(). It takes two arguments.  
  One is a state, Two is a ownProps

  - state is state from redux  
    if mapStateToProps return { state }, component get state as a prop
  - ownProps show props that component has.

- mapDispatchToProps is a function. It's a store.dispatch(). It takes two arguments.  
  One is a dispatch, Two is a ownProps
  - dispatch can change state  
    if mapDispatchToProps return { dispatch }, component get dipatch as a prop.  
    And dispatch is a function. Like a {toDos : state}, it can return {addToDo: text => dispatch(actionCreator.addToDo(text))}
  - ownProps show props that component has.

# Learning redux-tookit

- createAction() replace action

  **Before**

  ```
  const ADD = "ADD";

  const addToDo = (text) => {
    return {
      type: ADD,
      text,
    };
  };

  ```

  **After**

  ```
  const addToDo = createAction("ADD");

  ```

  **Before**

  ```
  const reducer = (state = [], action) => {
    switch (action.type) {
      case ADD:
        return [{ text: action.text, id: Date.now() }, ...state];
      case DELETE:
        return state.filter((toDo) => toDo.id !== action.id);
      default:
        return state;
    }
  };
  ```

  **After**

  ```
  const reducer = (state = [], action) => {
    switch (action.type) {
      case addToDo.type:
        return [{ text: action.payload, id: Date.now() }, ...state];
      case deleteToDo.type:
        return state.filter((toDo) => toDo.id !== action.payload);
      default:
        return state;
    }
  };

  ```

  Before createAction(), action's argument name was arbitrary.  
  After createAction(), action's argument is unified to 'payload'
