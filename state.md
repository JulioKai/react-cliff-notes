--------------------------------------------------------------
### State
--------------------------------------------------------------

**Using state case:**

Should only be used if you need to re-evaluate and re-render a component after a value changes, if it's only code manipulation it should suffice with normal js, it only "cares" and re-execute components when the state changes

The update function of setValue when using useState is not an "right away" change, it's schedule and modified in the next render (the value is not directly assigned)

If some data is going to change and that needs to be reflected in the user interface, we need to use state

--------------------------------------------------------------

**for manipulating state that is dependant of a part of a previously defined state:**

    const [state, setState] = useState('default value')

    setState((state) => `${state} is the previously assigned state`)  
    
this is a use case of the function way to modify state, the "normal" way is an assigment with setState('some state') but it's not used in this case because the function one ensures that the changed state get the latest snapshot before doing the change

--------------------------------------------------------------