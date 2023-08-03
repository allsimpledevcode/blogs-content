---
title: "Real-Time Network Status Monitoring/checking in React with TypeScript"
seoTitle: "Real-Time Network Status Monitoring/checking in React with TypeScript"
seoDescription: "Efficiently Monitor and Respond to Network Connectivity in Real-Time using React and TypeScript"
datePublished: Sun Jul 16 2023 08:16:18 GMT+0000 (Coordinated Universal Time)
cuid: clk55xd5t000209la5eyhe1iu
slug: real-time-network-status-monitoringchecking-in-react-with-typescript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689495105910/cc762a72-c305-4ff8-b5ec-0554391b5ec7.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689495301107/23f62f88-79b1-4ab6-880f-eca72cf7727a.png
tags: webdev, reactjs, typescript, beginners

---

Most people use to detect internet status using [`navigator.onLine`](http://navigator.onLine). but, it will not properly in some browsers and version.

For more info read the page: [navigator-online-not-always-working](%5D(https://stackoverflow.com/questions/14283124/navigator-online-not-always-working))

```typescript
import { useEffect, useState } from "react";
import "./styles.css";

export default function App() {
  const [isOnline, setIsOnline] = useState<boolean>(navigator.onLine);

  const checkApiStatus = async () => {
    try {
      const response = await fetch("https://www.boredapi.com/api/activity");
      setIsOnline(response.ok);
    } catch (error) {
      setIsOnline(false);
    }
  };

  const checkInternetConnection = () => {
    if (navigator.onLine) {
      checkApiStatus();
    } else {
      setIsOnline(false);
    }
  };

  useEffect(() => {
    window.addEventListener("online", checkInternetConnection);
    window.addEventListener("offline", checkInternetConnection);

    return () => {
      window.removeEventListener("online", checkInternetConnection);
      window.removeEventListener("offline", checkInternetConnection);
    };
  }, []);

  return (
    <div className="container">
      <h2>Internet connection status: {isOnline ? "Online" : "Offline"}</h2>
      <p>Turn on/off your internet connection to see what happens</p>
      {isOnline ? (
        <h1 className="online">You are Online</h1>
      ) : (
        <h1 className="offline">You are Offline</h1>
      )}
    </div>
  );
}
```

In this example, we use the useState hook to manage the network status state (isOnline) with an initial value of [navigator.onLine](http://navigator.onLine). The useEffect hook is used to add event listeners for the online and offline events. When the component is mounted, it registers the event listeners, and when the component is unmounted, it removes them to avoid memory leaks.

Whenever the network status changes, the corresponding event handler (checkInternetConnection) will be called, updating the isOnline state accordingly.

Finally, the component renders a heading displaying the current network status based on the value of isOnline.

**Live example**  

%[https://codesandbox.io/s/intetnet-status-s801xw] 

Remember to have TypeScript properly configured in your project for this code to work.