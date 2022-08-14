# useStorageState custom hooks

- A custom hooks to get storage state value by key and update the value by using setState

src/utils/type.ts

```ts
import { Dispatch, SetStateAction } from "react";

export type SetState<T> = Dispatch<SetStateAction<T>>;
```

src/utils/storage.ts

```ts
import { useEffect, useState } from "react";
import { SetState } from "./type";

interface Params<T> {
	storageKey: string;
	defaultValue: T;
}

export const useStorageState = <T>(params: Params<T>): [T, SetState<T>] => {
	const { storageKey, defaultValue } = params;
ed = window.localStorage.getItem(storageKey);
		if (stored === null) return defaultValue;
		return JSON.parse(stored) as T;
	});

	useEffect(() => {
		window.localStorage.setItem(storageKey, JSON.stringify(
	const [value, setValue] = useState<T>((): T => {
		const storvalue));
	}, [value, storageKey]);

	return [value, setValue];
};
```
