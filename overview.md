freeSP - Overview
=================

Many embedded systems are signal processing devices that shall
continuously operate in a larger context than the device itself. Not
rarely, these devices or the surrounding system consist of multiple
processing units, forming a heterogenuous distributed system of
collaborating processing nodes.

freeSP (**free** **S**ignal **P**rocessing) is a methodology to compose large
signal processing systems. It is strongly model based and comes with a
toolchain that integrates with GNU based build environments to
generate target code. freeSP has been used to build the target software
of a multi-functional front camera in an Automotive series project.

freeSP is free software under the BSD license (BSD 2-Clause License).

# Methodology

freeSP is model based and achieves complexity reduction by strict
model separation. It has three models which seamlessly join together
- behavior model
- component model
- platform model

The behavior model is a signal graph (or signal floating graph)
depicting the logical structure of the signal processing (sub-) system.
It is based on nodes which are instances of node type components and
which are linked together by edges (or connections) symbolizing the
transport of real data between computing entities. The behavior model
is to some degree independent from a real platform that executes it,
which means that the output of one signal graph running on one platform
is expected to be identical with the output of the same signal graph
running on a different platform.

The component model describes consistent component interfaces. Pecularly,
components may be composed from sub-components, described by a
signal graph.

The platform model holds all relevant information about the underlying
execution platform. It is a logical two-layer model of processes grouped
together to form archs. For example, a quadcore DSP running a bare-metal
firmware would form an arch having four processes. Another example
would be a hypervisor hosting multiple OS (each running multiple tasks),
which can be expressed by multiple archs (one for each OS) assigning
a process to each task. The platform model knows about data channels
between archs and processes which can be isochronous (e.g. sensor data),
asynchronous (e.g. network traffic) or closely coupled by shared memory.

freeSP provides tools to

- create and maintain models using a GUI based frontend (see
  [SGE](https://github.com/axel.freesp/sge/))
- validate models and check consistency
- process models and generate value (documentation, code etc.)

SGE, the GUI based frontend is written in Go using GTK+3. All other
model processing tools are written in XSLT and be processed by the
Apache Project XSLT Stylesheet processor XALAN.


