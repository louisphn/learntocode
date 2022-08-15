# Generics Typescript

- Reference:

  1. https://javascript.plainenglish.io/typescript-generics-whats-with-the-angle-brackets-4e242c567269
  2. https://stackoverflow.com/questions/48337555/confusion-about-angle-brackets-in-typescript

- A way to make type reusable, without having to specify the type of the generic. (dynamic type)

## Practical Application of Generics

Imagine you have the below types in your project.

```ts
export type AsyncGame = {
  item: Game;
  fulfilled?: boolean;
  loading?: boolean;
  error?: boolean;
};
export type AsyncGames = {
  items: Game[];
  fulfilled?: boolean;
  loading?: boolean;
  error?: boolean;
};
export type AsyncUserGame = {
  item: UserGame;
  fulfilled?: boolean;
  loading?: boolean;
  error?: boolean;
};
export type AsyncUserGames = {
  items: UserGame[];
  fulfilled?: boolean;
  loading?: boolean;
  error?: boolean;
};
```

// Game and UserGame are types we expect from different API
// responses.
It is very redundant. It is clear that they share a lot of commonalities in behavior.

Error-prone: See the network statuses fulfilled, loading, and, error are optional in all types. If we decide to change some of that behavior we have to update every type above. We may miss updating something.
Scalability: If we want to introduce a new type AsyncBrowseGames that wraps the BrowseGames type along with the network statuses, we will have to create more redundant code in our codebase. That will lead to more error-prone areas.

## Generics to rescue

Let's create a generic type as below

```ts
type AsyncData<T> = {
  data: T
  fulfilled?: boolean
  loading?: boolean
  error?: boolean
}
It receives a generic type parameter T and assigns it to one of its properties named data.

Now, we can create any number of types that wraps other types along with the network statuses.

type AsyncGames = AsyncData<Game[]>
type AsyncGame = AsyncData<Game | null>
type AsyncUser = AsyncData<User | null>
type AsyncUserGames = AsyncData<UserGame[]>
type AsyncBrowseGames = AsyncData<BrowseGame[]>
```
