# UseDebounce

This react hook declaratively returns a debounced stateful value given an input value. This is useful when combining searches with declarative fetch libraries such as [SWR](https://github.com/vercel/swr) or [react-refetch](https://github.com/heroku/react-refetch)

## Example

```typescript

export default Search() {
  const [searchQuery, setSearchQuery] = useState<string>('');

  // returns the latest value after 500ms to reduce unnecessary GET requests when typing
  const debouncedQuery = useDebounce<string>(seachQuery, 500);

  const { data: results } = swr(`/api/search?query=${debouncedQuery}`);

  return (
    <>
      <input type="text" value={searchQuery} onInput={(e) => setSearchQuery(e.target.value)}>
      <ul>
        {results.map((result) => <li>{result}</li>)}
      </ul>
    </>
  )

}

```
