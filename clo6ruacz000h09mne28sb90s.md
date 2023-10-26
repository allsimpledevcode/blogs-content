---
title: "Advanced Next.js URL handling with URLSearchParams"
datePublished: Thu Oct 26 2023 05:56:21 GMT+0000 (Coordinated Universal Time)
cuid: clo6ruacz000h09mne28sb90s
slug: advanced-nextjs-url-handling-with-urlsearchparams
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698299778851/4560c8e2-b8a5-4617-bcd3-03099f22bd4d.jpeg

---

## Video Tutorial

%[https://youtube.com/shorts/OcpXXmaSpo0?feature=shared]


## Introduction

In Next.js, you can work with URL query parameters using the next/router module, which provides a way to access and manipulate the query string parameters of the current URL. Query parameters are typically used to pass data from one page to another or to filter content on a page. Here's how you can work with URL query parameters in Next.js:

**Step 1:**
Setup next.js project. if you want more about it [read the article](https://simple-dev-code.blogspot.com/2023/10/step-by-step-guide-to-setting-up-nextjs.html)

**Step 2:**
Import URL search params in your file `page.tsx|jsx`.

```
import { useSearchParams } from 'next/navigation'
```
**Step 3:**
Use the useSearchParams hook into the file like below:
```
export default function Example() {
  const searchParams = useSearchParams()!;
}
```
**Step 4:**
Accessing query params value into your component:
```
export default function Example() {
  let term;
  
  const searchParams = useSearchParams()!;
  // Set updated value to the term
  if(searchParams?.has('term')) {
    term = searchParams.get('term');
  }

  return (
    <h1>Search term: {term}</h1>
  )
}
```
**Step 5:**
Now, in the browser url next to add the value like this `localhost:3000?term=tutorials`

It's will automatically show's in the page. refer the screenshot

![Demo](https://cdn.hashnode.com/res/hashnode/image/upload/v1698299777338/7292f7da-c2e2-4911-9ccd-7084e23201dd.png)


## Complete source code
```
'use client';

import { useState, useCallback } from 'react'
import { Dialog } from '@headlessui/react'
import { XMarkIcon, MagnifyingGlassIcon } from '@heroicons/react/24/outline'
import { useSearchParams, useRouter, usePathname } from 'next/navigation'

const navigation = [
  { name: 'Product', href: '#' },
  { name: 'Features', href: '#' },
  { name: 'Marketplace', href: '#' },
  { name: 'Company', href: '#' },
]

export default function Example() {
  let term;

  const router = useRouter()
  const pathname = usePathname()
  const [mobileMenuOpen, setMobileMenuOpen] = useState(false)
  
  const searchParams = useSearchParams()!;
  // Set updated value to the term
  if(searchParams?.has('term')) {
    term = searchParams.get('term');
  }
  
  const [searchTerm, setSearchTerm] = useState(term);  

  // Update Search params to url
  const createQueryString = useCallback(
    (name: string, value: string) => {
      const params = new URLSearchParams(searchParams)
      params.set(name, value)
 
      return params.toString()
    },
    [searchParams]
  )

  return (
    <main>
      <div className="bg-white dark:bg-slate-800">
        <header className="absolute inset-x-0 top-0 z-50">
          <nav className="flex items-center justify-between p-6 lg:px-8" aria-label="Global">
            <div className="flex lg:flex-1">
              <a href="#" className="-m-1.5 p-1.5">
                <span className="sr-only">Your Company</span>
                <img
                  className="h-8 w-auto"
                  src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600"
                  alt=""
                />
              </a>
            </div>
            <div className="flex lg:hidden">
                <div className="relative mt-2 rounded-md shadow-sm">
                  <div className="pointer-events-none absolute inset-y-0 left-0 flex items-center pl-2 text-black">
                    <MagnifyingGlassIcon width={16} height={15}/>
                  </div>
                  <input
                    type="text"
                    name="price"
                    value={searchTerm}
                    onBlur={(e) => {
                      router.push(pathname + '?' + createQueryString('term', e.target.value))
                    }}
                    onChange={(e) => {
                      setSearchTerm(e.target.value)
                    }}
                    id="price"
                    className="block w-full rounded-md border-0 py-1.5 pl-7 pr-20 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                    placeholder="Enter name"
                  />
                </div>
            </div>
            <div className="hidden lg:flex lg:gap-x-12">
              {navigation.map((item) => (
                <a key={item.name} href={item.href} className="text-sm font-semibold leading-6 text-gray-900 dark:text-white">
                  {item.name}
                </a>
              ))}
            </div>
            <div className="hidden lg:flex lg:flex-1 lg:justify-end">
              <div className="relative mt-2 rounded-md shadow-sm">
                <div className="pointer-events-none absolute inset-y-0 left-0 flex items-center pl-2 text-black">
                  <MagnifyingGlassIcon width={16} height={15}/>
                </div>
                <input
                  type="text"
                  name="price"
                  value={searchTerm}
                  onBlur={(e) => {
                    router.push(pathname + '?' + createQueryString('term', e.target.value))
                  }}
                  onChange={(e) => {
                    setSearchTerm(e.target.value)
                  }}
                  id="price"
                  className="block w-full rounded-md border-0 py-1.5 pl-7 pr-20 text-gray-900 ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                  placeholder="Enter name"
                />
              </div>
            </div>
          </nav>
          <Dialog as="div" className="lg:hidden" open={mobileMenuOpen} onClose={setMobileMenuOpen}>
            <div className="fixed inset-0 z-50" />
            <Dialog.Panel className="fixed inset-y-0 right-0 z-50 w-full overflow-y-auto bg-white px-6 py-6 sm:max-w-sm sm:ring-1 sm:ring-gray-900/10">
              <div className="flex items-center justify-between">
                <a href="#" className="-m-1.5 p-1.5">
                  <span className="sr-only">Your Company</span>
                  <img
                    className="h-8 w-auto"
                    src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600"
                    alt=""
                  />
                </a>
                <button
                  type="button"
                  className="-m-2.5 rounded-md p-2.5 text-gray-700"
                  onClick={() => setMobileMenuOpen(false)}
                >
                  <span className="sr-only">Close menu</span>
                  <XMarkIcon className="h-6 w-6" aria-hidden="true" />
                </button>
              </div>
              <div className="mt-6 flow-root">
                <div className="-my-6 divide-y divide-gray-500/10">
                  <div className="space-y-2 py-6">
                    {navigation.map((item) => (
                      <a
                        key={item.name}
                        href={item.href}
                        className="-mx-3 block rounded-lg px-3 py-2 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50"
                      >
                        {item.name}
                      </a>
                    ))}
                  </div>
                  <div className="py-6">
                    <a
                      href="#"
                      className="-mx-3 block rounded-lg px-3 py-2.5 text-base font-semibold leading-7 text-gray-900 hover:bg-gray-50"
                    >
                      Log in
                    </a>
                  </div>
                </div>
              </div>
            </Dialog.Panel>
          </Dialog>
        </header>

        <div className="relative isolate px-6 pt-14 lg:px-8">
          <div
            className="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80"
            aria-hidden="true"
          >
            <div
              className="relative left-[calc(50%-11rem)] aspect-[1155/678] w-[36.125rem] -translate-x-1/2 rotate-[30deg] bg-gradient-to-tr from-[#ff80b5] to-[#9089fc] opacity-30 sm:left-[calc(50%-30rem)] sm:w-[72.1875rem]"
              style={{
                clipPath:
                  'polygon(74.1% 44.1%, 100% 61.6%, 97.5% 26.9%, 85.5% 0.1%, 80.7% 2%, 72.5% 32.5%, 60.2% 62.4%, 52.4% 68.1%, 47.5% 58.3%, 45.2% 34.5%, 27.5% 76.7%, 0.1% 64.9%, 17.9% 100%, 27.6% 76.8%, 76.1% 97.7%, 74.1% 44.1%)',
              }}
            />
          </div>
          <div className="mx-auto max-w-2xl py-32 sm:py-48 lg:py-56">
            <div className="hidden sm:mb-8 sm:flex sm:justify-center">
              <div className="relative rounded-full px-3 py-1 text-sm leading-6 text-gray-600 ring-1 ring-gray-900/10 hover:ring-gray-900/20">
                Announcing our next round of funding.{' '}
                <a href="#" className="font-semibold text-indigo-600">
                  <span className="absolute inset-0" aria-hidden="true" />
                  Read more <span aria-hidden="true">&rarr;</span>
                </a>
              </div>
            </div>
            <div className="text-center">
              <h1 className="text-4xl font-bold tracking-tight text-gray-900 sm:text-6xl dark:text-white">
                Data to enrich your {term}
              </h1>
              <p className="mt-6 text-lg leading-8 text-gray-600">
                Anim aute id magna aliqua ad ad non deserunt sunt. Qui irure qui lorem cupidatat commodo. Elit sunt amet
                fugiat veniam occaecat fugiat aliqua.
              </p>
              <div className="mt-10 flex items-center justify-center gap-x-6">
                <a
                  href="#"
                  className="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                >
                  Get started
                </a>
                <a href="#" className="text-sm font-semibold leading-6 text-gray-900">
                  Learn more <span aria-hidden="true">→</span>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </main>
  )
}
```


That's all and Thanks for reading my article.


## Stay Updated with Our Latest Content!

If you found this article informative and valuable, consider subscribing to our YouTube channel for more insightful content, tutorials, and updates. By subscribing, you'll stay up-to-date with the latest developments in web development, technology, and much more.

[👉 Subscribe to Our Channel](https://youtube.com/@simpledevcode?feature=shared)

Don't miss out on the opportunity to expand your knowledge and skills. Join our growing community of learners and enthusiasts today!







