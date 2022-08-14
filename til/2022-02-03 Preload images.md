# Preload images custom hooks

```ts
export default function useImagePreloader(imageList: string[]) {
  const [imagesPreloaded, setImagesPreloaded] = useState<boolean>(false);
  useEffect(() => {
    let isCancelled = false;
    async function effect() {
      if (isCancelled) {
        return;
      }
      const imagesPromiseList: Promise<any>[] = [];
      // eslint-disable-next-line no-restricted-syntax
      for (const i of imageList) {
        imagesPromiseList.push(preloadImage(i));
      }
      await Promise.all(imagesPromiseList);
      if (isCancelled) {
        return;
      }
      setImagesPreloaded(true);
    }
    effect();
    return () => {
      isCancelled = true;
    };
  }, [imageList]);
  return { imagesPreloaded };
}
```

## Usage:

```tsx
import useImagePreloader from '~/utils/customHooks';
const Component = () => {
    const { imagesPreloaded } = useImagePreloader(textFileNames);

    if (!imagesPreloaded) return <p>Loading...</p>
    return (
      ...
    )
}
```
