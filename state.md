--------------------------------------------------------------
## State
--------------------------------------------------------------

### Using state case:

Should only be used if you need to re-evaluate and re-render a component after a value changes, if it's only code manipulation it should suffice with normal js, it only "cares" and re-execute components when the state changes

Other use is storing data inside a variable detached from the life cycle of the component function

State works per component instance basis, each component has their own

--------------------------------------------------------------

### Use state timing changes note:

The update function of setValue when using useState is not an "right away" change, it's schedule and modified in the next render (the value is not directly assigned)

If some data is going to change and that needs to be reflected in the user interface, we need to use state

    const [state, setState] = useState('value')

    const somethingHandler => {
        setState('new value')
        console.log(state)
} 

logs 'value' in the console, not 'new value' because the console.log runs before the new instance of the value in the re-render

--------------------------------------------------------------

### for manipulating state that is dependant of a part of a previously defined state:

    const [state, setState] = useState('default value')

    setState((state) => return `${state} is the previously assigned state`)  
    
this is a use case of the function way to modify state, the "normal" way is an assigment with setState('some state') but it's not used in this case because the function one ensures that the changed state get the latest snapshot before doing the change

--------------------------------------------------------------

### Two way bind

    const [val, setVal] = useState('')

    <form>
        <input type='text' onChange={somethingHandler} value={val}/>
    </form>

passing the state as a value in an input element is a two way data-bind in react

--------------------------------------------------------------

