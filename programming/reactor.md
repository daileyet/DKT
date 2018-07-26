# Reactor

## Overview

The Reactive Stream Spec is the specification that provides a standard for asynchronous programming for stream processing. This style of programming is more efficient regarding resources usage and fits amazingly with the new generation of machines with multiple cores.

## Components

### Publishers

The publishers are responsible for pushing data elements to the stream. It notifies the subscribers that a new piece of data is coming to the stream.

```java
/************************************************************************
 * Licensed under Public Domain (CC0)                                    *
 *                                                                       *
 * To the extent possible under law, the person who associated CC0 with  *
 * this code has waived all copyright and related or neighboring         *
 * rights to this code.                                                  *
 *                                                                       *
 * You should have received a copy of the CC0 legalcode along with this  *
 * work. If not, see <http://creativecommons.org/publicdomain/zero/1.0/>.*
 ************************************************************************/

package org.reactivestreams;

/**
 * A {@link Publisher} is a provider of a potentially unbounded number of sequenced elements, publishing them according to
 * the demand received from its {@link Subscriber}(s).
 * <p>
 * A {@link Publisher} can serve multiple {@link Subscriber}s subscribed {@link #subscribe(Subscriber)} dynamically
 * at various points in time.
 *
 * @param <T> the type of element signaled.
 */
public interface Publisher<T> {

    public void subscribe(Subscriber<? super T> s);

}
```

### Subscribers

The subscribers are responsible for making the data flow in the stream. When the publisher starts to send the piece of data on the data flow, the piece of data will be collected by the onNext\(T instance\) method, which is the parametrized interface.

```java
/************************************************************************
 * Licensed under Public Domain (CC0)                                    *
 *                                                                       *
 * To the extent possible under law, the person who associated CC0 with  *
 * this code has waived all copyright and related or neighboring         *
 * rights to this code.                                                  *
 *                                                                       *
 * You should have received a copy of the CC0 legalcode along with this  *
 * work. If not, see <http://creativecommons.org/publicdomain/zero/1.0/>.*
 ************************************************************************/

package org.reactivestreams;

/**
 * Will receive call to {@link #onSubscribe(Subscription)} once after passing an instance of {@link Subscriber} to {@link Publisher#subscribe(Subscriber)}.
 * <p>
 * No further notifications will be received until {@link Subscription#request(long)} is called.
 * <p>
 * After signaling demand:
 * <ul>
 * <li>One or more invocations of {@link #onNext(Object)} up to the maximum number defined by {@link Subscription#request(long)}</li>
 * <li>Single invocation of {@link #onError(Throwable)} or {@link Subscriber#onComplete()} which signals a terminal state after which no further events will be sent.
 * </ul>
 * <p>
 * Demand can be signaled via {@link Subscription#request(long)} whenever the {@link Subscriber} instance is capable of handling more.
 *
 * @param <T> the type of element signaled.
 */
public interface Subscriber<T> {

    public void onSubscribe(Subscription s);

    public void onNext(T t);

    public void onComplete();
}
```

## categories

There are two categories of reactive sequences—hot and cold.

### Cold

The cold publishers start to generate data only if it receives a new subscription. If there are no subscriptions, the data never comes to the flow.

### Hot

The hot publishers do not need any subscribers to generate the data flow. When the new subscriber is registered, the subscriber will only get the new data elements emitted.

## Reactive types

There are two reactive types which represent the reactive sequences.

### Mono

a single value or empty 0\|1

### Flux

a sequence of 0\|N items

