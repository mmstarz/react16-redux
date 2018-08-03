# example of using 'react-redux', 'redux', redux-thunk.
# link: https://mmstarz.github.io/react16-redux/
# watch console or/and redux-extension to see how it works.
# features used:
  
  *import { createStore, combineReducers, applyMiddleware, compose } from 'redux';
  *import { Provider } from 'react-redux';
  *import { connect } from 'react-redux';
  *import thunk from 'redux-thunk';
  
  const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;

  separate files for:
    actionTypes,
    counter (increment, decrement, add, subtract) as actionCreators,
    result actions:
      deleteResult as actionCreators,
      storeResult as async middleware wich returns dispatch saveResult action.
  
  all action files are exported with:
    import * as actionCreators from '../../store/actions/index';
