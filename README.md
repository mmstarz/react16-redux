# react16-redux-basics
# link: https://mmstarz.github.io/react16-redux/
# example of using 'react-redux', 'redux'.
# features used:
  /* index.js */
  ...
  import { createStore, combineReducers } from 'redux';
  import { Provider } from 'react-redux';  
  import counterReducer from '../src/store/reducers/counter';
  import resultReducer from '../src/store/reducers/result';

  const rootReducer = combineReducers({
    global_counter: counterReducer,
    global_result: resultReducer,
  });

  const store = createStore(rootReducer);

  ReactDOM.render(<Provider store={store}><App /></Provider>, document.getElementById('root'));

  /* Counter.js */
  import { connect } from 'react-redux';
  ...
  import * as actionTypes from '../../store/actions';
  ...
  const mapStateToProps = state => {
    return {
        localCounter: state.global_counter.counter,
        storedResults: state.global_result.result,
    }
  }

  const mapDispatchToProps = dispatch => {
    return {
        onIncrementCounter: () => dispatch({type: actionTypes.INCREMENT}),
        onDecrementCounter: () => dispatch({type: actionTypes.DECREMENT}),
        onAddCounter: () => dispatch({type: actionTypes.ADD, value: 5}),
        onSubtractCounter: () => dispatch({type: actionTypes.SUBTRACT, value: 5}),
        onStoreResult: (result) => dispatch({type: actionTypes.STORE_RESULT, result: result}),
        onDeleteResult: (id) => dispatch({type: actionTypes.DELETE_RESULT, elementID: id}),
    }
  }

  export default connect(mapStateToProps, mapDispatchToProps)(Counter);
