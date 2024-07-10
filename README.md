# react-show-on-scroll-hook-ts
This react hook will use an intersection observer to change show state to true when a sentinel element intersects with the viewport.

For a working example, view the code sandbox [here](https://codesandbox.io/p/devbox/react-useshowonscroll-ts-99twt8), or see below.

**Example usage:**

```
import React, { useState } from "react";
import { useShowOnScroll } from "./hooks/useShowOnScroll";

const ExampleHookConsumer: React.FC = () => {
  const [show, setShow] = useState(false);
  const sentinelRef = useShowOnScroll(show, setShow);

  return (
    <div>
      {show && (
        <div>
          Hello there!
        </div>
      )}
      <div ref={sentinelRef} />
    </div>
  );
};

export default ExampleHookConsumer;
```
