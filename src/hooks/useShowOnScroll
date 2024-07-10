import {
  useEffect,
  useRef,
  MutableRefObject,
  Dispatch,
  SetStateAction,
} from "react";

const defaultOptions: IntersectionObserverInit = {
  root: null,
  rootMargin: "0px",
  threshold: 0,
};

export function useShowOnScroll(
  show: boolean,
  setShow: Dispatch<SetStateAction<boolean>>,
  options: IntersectionObserverInit = defaultOptions,
): MutableRefObject<HTMLDivElement | null> {
  const sentinelRef = useRef<HTMLDivElement | null>(null);
  const optionsRef = useRef(options);

  useEffect(() => {
    if (!show) {
      const observer = new IntersectionObserver((entries, observerInstance) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            setShow(true);
            observerInstance.unobserve(entry.target);
          }
        });
      }, optionsRef.current);

      if (sentinelRef.current) {
        observer.observe(sentinelRef.current);
      }

      return () => {
        observer.disconnect();
      };
    }
  }, [show, setShow]);

  return sentinelRef;
}
