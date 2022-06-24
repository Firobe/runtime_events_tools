A collection of observability tools around the runtime events tracing system
introduced in OCaml 5.0.

## olly

`olly` will report the GC tail latency profile of an OCaml executable.

```bash
$ olly 'menhir -v --table sysver.mly'
<snip>
GC latency profile:
#[Mean (ms):    0.03,    Stddev (ms):   0.25]
#[Min (ms):     0.00,    max (ms):      39.75]

Percentile       Latency (ms)
25.0000          0.00
50.0000          0.00
60.0000          0.00
70.0000          0.00
75.0000          0.00
80.0000          0.00
85.0000          0.00
90.0000          0.00
95.0000          0.04
96.0000          0.16
97.0000          0.26
98.0000          0.50
99.0000          0.77
99.9000          2.66
99.9900          4.48
99.9990          7.65
99.9999          39.75
100.0000         39.75
```

`olly` can also record the runtime trace log in Chrome tracing format.

```bash
$ olly -t menhir_sysver.trace 'menhir -v --table sysver.mly'
$ ls menhir_sysver.trace
menhir_sysver.trace
```

This trace can be viewed in [perfetto trace viewer](https://ui.perfetto.dev/).

## Dependencies

The library depends on
[`hdr_histogram_ocaml`](https://github.com/kayceesrk/hdr_histogram_ocaml).
