### `useCallback`闭包问题

【存在的问题】：闭包，如果里面的函数访问的值为非依赖项的值，则访问到的是闭包里原来的值

【解决】：核心思想：利用`useRef`

```js
function useBind(value){
    let ref = useRef(value)
    useEffect = (()=>{
        ref.current = value
    }) 
    return current
}

function component(){
    let [values,setValues] = useState()
    let payLoad = useBind(values)
    
    //这样就能确保payLpad不变，cb不变，child组件不更新。且访问到的value值永远是最新的而不是闭包里的
    let cb = useCallback(()=>{
        console.log(payLoad.current)
    },[payLoad])
    
    return <Child fn = cb />
}
```



### `useContext + useReducer + useMemo`

【参考链接】http://www.ptbird.cn/react-createContex-useContext.html

