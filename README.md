Brand new pintos for Operating Systems and Lab (CS330), KAIST, by Youngjin Kwon.

The manual is available at https://casys-kaist.github.io/pintos-kaist/.

### busy wait
```
// result: make check

pass tests/threads/alarm-single
pass tests/threads/alarm-multiple
pass tests/threads/alarm-simultaneous
FAIL tests/threads/alarm-priority
pass tests/threads/alarm-zero
pass tests/threads/alarm-negative
FAIL tests/threads/priority-change
FAIL tests/threads/priority-donate-one
FAIL tests/threads/priority-donate-multiple
FAIL tests/threads/priority-donate-multiple2
FAIL tests/threads/priority-donate-nest
FAIL tests/threads/priority-donate-sema
FAIL tests/threads/priority-donate-lower
FAIL tests/threads/priority-fifo
FAIL tests/threads/priority-preempt
FAIL tests/threads/priority-sema
FAIL tests/threads/priority-condvar
FAIL tests/threads/priority-donate-chain
FAIL tests/threads/mlfqs/mlfqs-load-1
FAIL tests/threads/mlfqs/mlfqs-load-60
FAIL tests/threads/mlfqs/mlfqs-load-avg
FAIL tests/threads/mlfqs/mlfqs-recent-1
FAIL tests/threads/mlfqs/mlfqs-fair-2
FAIL tests/threads/mlfqs/mlfqs-fair-20
FAIL tests/threads/mlfqs/mlfqs-nice-2
FAIL tests/threads/mlfqs/mlfqs-nice-10
FAIL tests/threads/mlfqs/mlfqs-block
22 of 27 tests failed.
```
```
// result: run alarm-single

Executing 'alarm-single':
...
Execution of 'alarm-single' complete.
Timer: 285 ticks
Thread: 0 idle ticks, 286 kernel ticks, 0 user ticks
```
```
// result: run alarm-multiple

Executing 'alarm-multiple':
...
Execution of 'alarm-multiple' complete.
Timer: 620 ticks
Thread: 0 idle ticks, 621 kernel ticks, 0 user ticks
```
### # 1 
- busy wait 방식을 sleep wakeup 로 수정
- 
```
// result: make check

pass tests/threads/alarm-single
pass tests/threads/alarm-multiple
pass tests/threads/alarm-simultaneous
FAIL tests/threads/alarm-priority
pass tests/threads/alarm-zero
pass tests/threads/alarm-negative
FAIL tests/threads/priority-change
FAIL tests/threads/priority-donate-one
FAIL tests/threads/priority-donate-multiple
FAIL tests/threads/priority-donate-multiple2
FAIL tests/threads/priority-donate-nest
FAIL tests/threads/priority-donate-sema
FAIL tests/threads/priority-donate-lower
FAIL tests/threads/priority-fifo
FAIL tests/threads/priority-preempt
FAIL tests/threads/priority-sema
FAIL tests/threads/priority-condvar
FAIL tests/threads/priority-donate-chain
FAIL tests/threads/mlfqs/mlfqs-load-1
FAIL tests/threads/mlfqs/mlfqs-load-60
FAIL tests/threads/mlfqs/mlfqs-load-avg
FAIL tests/threads/mlfqs/mlfqs-recent-1
FAIL tests/threads/mlfqs/mlfqs-fair-2
FAIL tests/threads/mlfqs/mlfqs-fair-20
FAIL tests/threads/mlfqs/mlfqs-nice-2
FAIL tests/threads/mlfqs/mlfqs-nice-10
FAIL tests/threads/mlfqs/mlfqs-block
22 of 27 tests failed.
```
```
// result: run alarm-single

Executing 'alarm-single':
...
Execution of 'alarm-single' complete.
Timer: 289 ticks
Thread: 250 idle ticks, 40 kernel ticks, 0 user ticks
```
```
// result: run alarm-multiple

Executing 'alarm-multiple':
...
Execution of 'alarm-multiple' complete.
Timer: 628 ticks
Thread: 550 idle ticks, 79 kernel ticks, 0 user ticks
```
### # 2
- 쓰레드 우선순위가 바뀌어서 CPU 를 선점해야 하는 경우
  - thread_create 이후 (새로 생성된 쓰레드와 우선순위 비교)
  - thread_set_priority 이후 
```
pass tests/threads/alarm-single
pass tests/threads/alarm-multiple
pass tests/threads/alarm-simultaneous
pass tests/threads/alarm-priority
pass tests/threads/alarm-zero
pass tests/threads/alarm-negative
pass tests/threads/priority-change
FAIL tests/threads/priority-donate-one
FAIL tests/threads/priority-donate-multiple
FAIL tests/threads/priority-donate-multiple2
FAIL tests/threads/priority-donate-nest
FAIL tests/threads/priority-donate-sema
FAIL tests/threads/priority-donate-lower
pass tests/threads/priority-fifo
pass tests/threads/priority-preempt
FAIL tests/threads/priority-sema
FAIL tests/threads/priority-condvar
FAIL tests/threads/priority-donate-chain
FAIL tests/threads/mlfqs/mlfqs-load-1
FAIL tests/threads/mlfqs/mlfqs-load-60
FAIL tests/threads/mlfqs/mlfqs-load-avg
FAIL tests/threads/mlfqs/mlfqs-recent-1
FAIL tests/threads/mlfqs/mlfqs-fair-2
FAIL tests/threads/mlfqs/mlfqs-fair-20
FAIL tests/threads/mlfqs/mlfqs-nice-2
FAIL tests/threads/mlfqs/mlfqs-nice-10
FAIL tests/threads/mlfqs/mlfqs-block
18 of 27 tests failed.
```
### # 3
- Priority Scheduling-Synchronization
```
pass tests/threads/alarm-single
pass tests/threads/alarm-multiple
pass tests/threads/alarm-simultaneous
pass tests/threads/alarm-priority
pass tests/threads/alarm-zero
pass tests/threads/alarm-negative
pass tests/threads/priority-change
FAIL tests/threads/priority-donate-one
FAIL tests/threads/priority-donate-multiple
FAIL tests/threads/priority-donate-multiple2
FAIL tests/threads/priority-donate-nest
FAIL tests/threads/priority-donate-sema
FAIL tests/threads/priority-donate-lower
pass tests/threads/priority-fifo
pass tests/threads/priority-preempt
pass tests/threads/priority-sema
pass tests/threads/priority-condvar
FAIL tests/threads/priority-donate-chain
FAIL tests/threads/mlfqs/mlfqs-load-1
FAIL tests/threads/mlfqs/mlfqs-load-60
FAIL tests/threads/mlfqs/mlfqs-load-avg
FAIL tests/threads/mlfqs/mlfqs-recent-1
FAIL tests/threads/mlfqs/mlfqs-fair-2
FAIL tests/threads/mlfqs/mlfqs-fair-20
FAIL tests/threads/mlfqs/mlfqs-nice-2
FAIL tests/threads/mlfqs/mlfqs-nice-10
FAIL tests/threads/mlfqs/mlfqs-block
16 of 27 tests failed.
```
### # 4
- Priority Donation
```
pass tests/threads/alarm-single
pass tests/threads/alarm-multiple
pass tests/threads/alarm-simultaneous
pass tests/threads/alarm-priority
pass tests/threads/alarm-zero
pass tests/threads/alarm-negative
pass tests/threads/priority-change
pass tests/threads/priority-donate-one
pass tests/threads/priority-donate-multiple
pass tests/threads/priority-donate-multiple2
pass tests/threads/priority-donate-nest
pass tests/threads/priority-donate-sema
pass tests/threads/priority-donate-lower
pass tests/threads/priority-fifo
pass tests/threads/priority-preempt
pass tests/threads/priority-sema
pass tests/threads/priority-condvar
pass tests/threads/priority-donate-chain
FAIL tests/threads/mlfqs/mlfqs-load-1
FAIL tests/threads/mlfqs/mlfqs-load-60
FAIL tests/threads/mlfqs/mlfqs-load-avg
FAIL tests/threads/mlfqs/mlfqs-recent-1
FAIL tests/threads/mlfqs/mlfqs-fair-2
FAIL tests/threads/mlfqs/mlfqs-fair-20
FAIL tests/threads/mlfqs/mlfqs-nice-2
FAIL tests/threads/mlfqs/mlfqs-nice-10
FAIL tests/threads/mlfqs/mlfqs-block
9 of 27 tests failed.
```