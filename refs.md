--------------------------------------------------------------
## Refs
--------------------------------------------------------------

### common case for ref use and general notation:

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

