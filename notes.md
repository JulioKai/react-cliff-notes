
## React quicknotes and cheatsheet


--------------------------------------------------------------
### Props
--------------------------------------------------------------

**passing props from parent to children component:**

    parent:
        <Element propName='value' propName2='value2' />

    component:
        const Element = (props) => {
            return (
                <p>{props.propName1} {props.propName2}</p>
            )
        } 
        
recives props as an argument and can be used as propierties of the object that recives as argument

--------------------------------------------------------------

**creating a wrapper or passing other jsx elements into a component:**

    parent where is called: 
        <CompContainer>
            <h1>someTitle</h1>
            <p>someParagraph</p>
        </CompContainer>

    component:
        const CompContainer = (props) => {
            return (
                <div class="some stylishing classses for ex">{props.children}</div>
            )
        } 
        
recives props as arguments, uses the reserved propierty of props called children to indicate where the nested html elements will go (the h1 and p for ex)

--------------------------------------------------------------

**passing things like classes or functions to a child component:**

    parent: 
        <Button className='clase1 clase2' onClick={someCBFunction} text='texto del boton'/>

    component: 
        const Button = (props) => {
            const classes = 'clase3' + props.className
            return (
                <button className={classes} onClick={props.onClick}> props.text </button>
            )
        } 
        
they have redifined inside the custom component inside the corresponding atribute 

--------------------------------------------------------------
### Event Listeners
--------------------------------------------------------------

**for adding functions to event listeners:**

    in a given component:
        const functionHandler = () => {console.log('hi)}

        return (
            <button onClick={functionHandler}>text</button>
        ) 
        
has to recive functions, it doesn't just executes some code it HAS to be a function, also it passes as a reference, not execution [it's functionHandler, not functionHandler()] 

--------------------------------------------------------------

**for adding functions with params to event listeners:**

    in a given component: 

        const testHandler = (param, param2) => {
                console.log(param, param2)
            }

        return (
            <button onClick={() => {handlerOfTestHandlers(1, 2)})>test</button>
            ) 
            
to pass params within a function on an event listener you have to pass a function that has a callback or a "running" function as part of the execution to be able to pass the parameters without executing the function (notice how unlike a function reference, a function with parameters is passed inside an anonymous function and that anon is the reference function)

**if you neeed to run multiple example:**

    const handlerOfTestHandlers = (param, param2, param3, param4, param5, param6) => {
        testHandler(param, param2)
        testHandler2(param3, param4)
        testHandler3(param5, param6)
    } 
    
you can group functions inside a handler and call it the same way with multiple params

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
### Refs
--------------------------------------------------------------

**common case for ref use and general notation:**

    const emailRef = useRef()
    const passwordlRef = useRef()

    return (
        <input ref={emailRef} type='email' id='email'></input>
        <input ref={passwordlRef} type='password' id='password'></input>
    )

    to access the values: 
        emailRef.current.value
        passwordRef.current.value

Using refs instead of state solves the problem of re-rendering the component in each modification (for example) in an input that would appear if we use state instead

--------------------------------------------------------------

