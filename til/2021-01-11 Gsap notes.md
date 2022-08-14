# Fix scroll trigger on resize:

```jsx
  useEffect(() => {
    gsap.registerPlugin(ScrollTrigger);
    if (imagesRef.current.length > 0) {
      accordionsRef.current.forEach((item, index) => {
        const tl = gsap
          .timeline()
          .to(imagesRef.current[index] as HTMLDivElement, {
            height: window.innerWidth >= 768 ? spaceBetween : spaceBetween + 64,
            duration: 2,
            ease: 'none',
          });
        ScrollTrigger.config({
          autoRefreshEvents: 'visibilitychange,DOMContentLoaded,load',
        });
        ScrollTrigger.create({
          trigger: item,
          scrub: 0.2,
          start: getPosition(index),
          end: '+=80',
          animation: tl,
          invalidateOnRefresh: true,
        });
      });
    }
    return () => {
      ScrollTrigger.getAll().forEach((st) => st.kill());
    };
  }, [getPosition, imagesRef, spaceBetween]);
```
