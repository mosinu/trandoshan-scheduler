# scheduler

[![Build Status](https://travis-ci.org/trandoshan-io/scheduler.svg?branch=master)](https://travis-ci.org/trandoshan-io/scheduler)
[![Go Report Card](https://goreportcard.com/badge/github.com/trandoshan-io/scheduler)](https://goreportcard.com/report/github.com/trandoshan-io/scheduler)
[![Maintainability](https://api.codeclimate.com/v1/badges/25d591c24d83b929e63f/maintainability)](https://codeclimate.com/github/trandoshan-io/scheduler/maintainability)

Scheduler is a Go written program designed to orchestrate resource parsing

## features

- use scalable messaging protocol (nats)

## how it work

- The Scheduler process connect to a nats server (specified by env variable *NATS_URI*) 
and set-up a subscriber for message with tag *doneSubject*
- When an URL is received the scheduler will apply list of *crawling rules* to determinate if resource is to be crawled
- If resource should be crawled to scheduler will sent the url to nats with subject *todoSubject* for the crawlers

## crawling rules

Here is the rules that determinate if crawling is to be done:

- Url has not been already crawled