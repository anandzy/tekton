# Let's Tekton

![Tekton](https://tekton.dev/images/tekton-horizontal-color.png)


## _Overview_
- Tekton is an open-source cloud native CI/CD (Continuous Integration and Delivery/Deployment) solution. It allows developers to build, test, and deploy across destinations using a Kubernetes cluster of their own.

- The Tekton project, at this moment, consists of 4 components:

    - Pipelines: Basic building blocks (tasks and pipelines) of a CI/CD workflow
    - Triggers: Event triggers for a CI/CD workflow
    - CLI: Command-line interface for CI/CD workflow management
    - Dashboard: General-purpose, web-based UI for Pipelines
- Pipelines, of all the components, provides the core functionality of Tekton and sets the foundation for the other components. Installation of Triggers, CLI, and Dashboard is optional; you may set them up in conjunction with Pipelines to create   the CI/CD workflow that works best for your team and project.

- In addition, the project provides a service, Tekton Catalog, which features common blocks of CI/CD workflows that one may mix and match in their own project.

<br/>

<br/>

## How Tekton works
- Loosely speaking, at its core, Tekton Pipelines functions by wrapping each of your steps. More specifically, Tekton Pipelines injects an entrypoint binary in step containers, which executes the command you specify when the system is ready.

- Tekton Pipelines tracks the state of your pipeline using Kubernetes Annotations. These annotations are projected inside each step container in the form of files with the Kubernetes Downward API. The entrypoint binary watches the projected files closely, and will only start the provided command if a specific annotation appears as files. For example, when you ask Tekton to run two steps consecutively in a task, the entrypoint binary injected into the second step container will wait idly until the annotations report that the first step container has successfully completed.

- In addition, Tekton Pipelines schedules some containers to run automatically before and after your step containers, so as to support specific built-in features, such as the retrieval of input resources and the uploading of outputs to blob storage solutions. You can track their running statuses as well via taskRuns and pipelineRuns. The system also performs a number of other operations to set up the environment before running the step containers; for more information, see Tasks and Pipelines.
<br/>

<br/>


![Alt text](docs/images/runtime.png?raw=true "flow")

<br/>

<br/>

### Tasks and Pipelines are Building Blocks of Tekton CI/CD Workflow

### Tekton Pipelines
- Tekton Pipelines is a Kubernetes extension that installs and runs on your Kubernetes cluster. It defines a set of Kubernetes Custom Resources that act as building blocks from which you can assemble CI/CD pipelines. Once installed, Tekton Pipelines becomes available via the Kubernetes CLI (kubectl) and via API calls, just like pods and other resources. Tekton is open-source and part of the CD Foundation, a Linux Foundation project.

<br/>

<br/>

### Tekton Pipelines entities
- Tekton Pipelines defines the following entities:

| Entity | Description |
| ------ | ------ |
| Task | Defines a series of steps which launch specific build or delivery tools that ingest specific inputs and produce specific outputs. |
| TaskRun |	Instantiates a Task for execution with specific inputs, outputs, and execution parameters. Can be invoked on its own or as part of a Pipeline. |
| Pipeline | Defines a series of Tasks that accomplish a specific build or delivery goal. Can be triggered by an event or invoked from a PipelineRun. |
| PipelineRun |	Instantiates a Pipeline for execution with specific inputs, outputs, and execution parameters. |
| PipelineResource	| Defines locations for inputs ingested and outputs produced by the steps in Tasks. |
| Run (alpha) |	Instantiates a Custom Task for execution when specific inputs. |

<br/>

<br/>

## Prerequisite
Not mandatory
| Software | version | env |
| ------ | ------ | ------ |
| minikube | v1.11.0 | Linux |
| k8s | v1.18.3 | local |
| tekton client version | 0.17.0 | local |
| tekton Pipeline version | v0.22.0 | local |

<br/>

<br/>

## _Installation & Documentation_
- [Installation of Tekton CLI](https://tekton.dev/docs/cli/)
- [Installation of Tekton Pipelines & Webhooks on k8s](https://tekton.dev/docs/getting-started/)
- [Installation of Triggets](https://github.com/tektoncd/triggers/blob/main/docs/install.md)

## _Tutorials_
- [Tekton Pipelines Tutorial](https://github.com/tektoncd/pipeline/blob/main/docs/tutorial.md)
- [Creating CI Pipelines with Tekton](https://www.arthurkoziel.com/creating-ci-pipelines-with-tekton-part-1/)


## _Helpful explanation_
- [Tasks](https://tekton.dev/docs/pipelines/tasks/#overview)
- [Events](https://tekton.dev/docs/pipelines/tasks/#defining-steps)
- [Pipelines](https://tekton.dev/docs/pipelines/pipelines/)

