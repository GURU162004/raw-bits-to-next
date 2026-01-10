Why I’m making this:

I’m tired of people misunderstanding Next.js. Modern web engineers blame Next.js or Vercel for broken pages, hydration bugs, ISR loops, streaming issues, or slow LCP. They cry about the framework when the real problem is their own lack of understanding and skill issues.

Most devs do not understand the runtime execution graph, cache layers, ISR mechanics, RSC protocol, Edge vs Node differences, or streaming hydration.

I want to make people understand what happens under the hood. It may feel overwhelming at first, but trust me—you’ll fall in love with Next.js for its beauty.

This track lets you:

See exactly how Next.js works under the hood.

Understand why App Router behaves differently from Page Router.

Reason like a framework engineer.

Never get confused by layouts, intercepting routes, parallel slots, metadata, streaming, or hydration.

Debug any Next.js app like a god without blaming the framework for things it does correctly.

Build the same deep knowledge engineers at Vercel have, so you can fix what modern web devs fail at lol


It continues the ideas from this repo: (https://github.com/renderhq/raw-bits-to-react)
 and goes deeper, teaching real engine-level understanding.

Week 1 – Runtime Architecture and Request Lifecycle

Goal: Understand how Next.js executes requests
Reason: Most modern engineers misinterpret runtime behavior, blame Edge cold starts or Node caching without understanding execution

Topics:

Incoming request router match

Decide execution target: static file / Edge runtime / Node runtime

Middleware interception

Rendering strategy selection

Node runtime: full APIs, long-lived processes

Edge runtime: V8 isolate, fetch-only, no fs, no sockets

Cold start behavior: Edge vs Node

Execution graph: request → middleware → route handler → RSC tree → render → stream → hydrate

Project: Instrument full lifecycle, measure cold vs warm

Week 2 – File-Based Routing Engine

Goal: Master URL to layout/page resolution
Reason: Devs get confused about layouts, intercepting routes, parallel routes, then blame Next.js

Topics:

Folder to route mapping

page.tsx, layout.tsx, template.tsx

Parallel routes using @slot

Intercepting routes using (..)

Route resolution rules: static, dynamic, catch-all, optional

Metadata extraction: static, dynamic

Streaming metadata to head

Project: Build a router that resolves URLs, layouts, pages, slots

Week 3 – Rendering Models and ISR

Goal: Understand SSG, SSR, ISR, partial rendering
Reason: Engineers blame stale data, hydration glitches, or slow pages without knowing ISR mechanics

Topics:

SSG: build-time snapshot, static dependency graph

SSR: per-request execution, streaming, cache boundaries

ISR: stale-while-revalidate, background regeneration, race conditions

Partial Rendering: static shell, dynamic islands, cache tagging

Project: Implement ISR with file-backed cache revalidation workers

Week 4 – React Server Components (RSC)

Goal: Internalize RSC, the heart of Next.js
Reason: Modern engineers misuse hooks, server actions, streaming, then complain about Next.js complexity

Topics:

Server-only component graph

No client hooks

Serialization protocol: Flight

Server render Flight payload → client rehydrate

use server, server actions, argument serialization, security, mutation invalidation

Progressive streaming, Suspense boundaries, backpressure

Project: Implement a mini RSC protocol to serialize component trees and stream

Week 5 – Middleware and Edge Runtime

Goal: Master pre-routing logic and Edge constraints
Reason: People blame slow Edge responses or inconsistent middleware without knowing headers, caching, and V8 isolates

Topics:

Middleware runs before routing

Edge runtime: no fs, no sockets, fetch-only

Header rewrites, redirects, auth, geo, A/B testing

Edge caching: keys, TTL, regional consistency

Streaming responses: early flush

Project: Middleware rewrite routes based on country/device

Week 6 – Data Fetching and Caching Internals

Goal: Understand fetch wrapping, cache layers, waterfall elimination
Reason: Developers blame Next.js for double-fetch waterfalls, stale caches instead of understanding internal fetch behavior

Topics:

Fetch wrapping, request deduplication

Cache modes: force-cache, no-store, revalidate

Cache layers: request, route data

Tag-based invalidation

Parallel execution, Suspense-based fetching, cache boundary placement

Project: Visualize fetch graph and remove waterfalls

Week 7 – Bundling and Code Splitting

Goal: Understand server/client bundle separation, tree shaking
Reason: Devs misconfigure client/server code, blame Next.js bundling

Topics:

SWC transforms

RSC splitting

Server/client bundles

Chunking: route-based, layout reuse, dynamic import

Tree shaking: server-only elimination, client boundary enforcement

Project: Build bundle visualizer for App Router chunks

Week 8 – Hydration and Client Boot

Goal: Master selective and streaming hydration
Reason: Modern devs blame Next.js for hydration mismatches, double renders, without understanding event replay and Suspense

Topics:

HTML first, JS later streaming

Selective and priority hydration

Event replay

Failure modes: mismatched trees, double render, non-deterministic data

Project: Create intentional hydration mismatches and fix them

Week 9 – Performance Engineering

Goal: Tune Next.js apps to sub-second LCP, 60fps under load
Reason: Devs blame Next.js/Vercel instead of boundary placement, RSC streaming, caching

Topics:

Metrics: TTFB, LCP, INP, CLS

Route-level caching, image optimizer, font loader, script strategies

Avoid server-client thrashing, layout containment, RSC boundary placement

Project: Reduce LCP from 3s to under 1s without hacks

Week 10 – Debugging Like a Real Engineer

Goal: Break and fix everything
Reason: Modern engineers cry about ISR loops, Suspense deadlocks, RSC cache poisoning without understanding internal mechanics

Topics:

RSC cache poisoning, ISR loops, Edge/Node divergence, Suspense deadlocks, double fetches

Tools: NEXT_DEBUG, Flight inspection, render pipeline logs

Project: Break Next.js app 10 ways and repair all

Weeks 11-12 – Capstone

Goal: Build a fully understood, production-ready Next.js stack
Reason: So you know why devs fail, why modern web complains, and can confidently fix anything

Deliverables:

Custom App Router

RSC streaming renderer

ISR cache tagging

Edge middleware engine

Bundle analyzer

Performance dashboard

Constraints:

LCP under 1s

10k+ updates

Zero hydration errors

Works on Edge/Node

Outcome:

You do not just use Next.js—you reason about it

You can confidently say: “I fix broken Next.js apps”
