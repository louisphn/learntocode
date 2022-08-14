Use media query custom hooks

```jsx
import { useState, useEffect } from "react";
const useMediaQuery = (query) => {
  const [matches, setMatches] = useState(false);
  useEffect(() => {
    const media = window.matchMedia(query);
    if (media.matches !== matches) {
      setMatches(media.matches);
    }
    const listener = () => setMatches(media.matches);
    window.addEventListener("resize", listener);
    return () => window.removeEventListener("resize", listener);
  }, [matches, query]);
  return matches;
};
export default useMediaQuery;
```

## Usage

```jsx
import useMediaQuery from "~/hooks/useMediaQuery";
export const Component = () => {
  const isDesktop = useMediaQuery("(min-width: 960px)");
};
```
