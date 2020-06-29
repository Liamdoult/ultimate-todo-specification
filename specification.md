# 1. Definitions
## 1.1 Ultimate TODO Document
A document that defines or describes a list of tasks (also know as a TODO list). An Ultimate TODO definition uses and conforms to the Ultimate TODO Specification

# 2 Specification 

In the following description, if a field is not explicitly __REQUIRED__ or described with a _MUST_ or _SHALL_, it can be considered _OPTIONAL_.

## 2.1 Data Types

The formats defined by Ultimate TODO are:

| type | format | Comments |
| :-- | :-- | :-- |
| string | | |
| string | date | As defined by `full-date` - RFC3339 |
| string | date-time | As defined by `date-time` - RFC3339 |
| boolean | | |

## 2.2 Rich Text Formatting

Throughout the specification `description` fields are noted as supporting CommonMark markdown formatting. Where Ultimate-TODO tooling renders rich text it _MUST_ support, at a minimum, markdown syntax as described by [CommonMark 0.27](https://spec.commonmark.org/0.27/). Tooling _MAY_ choose to ignore some CommonMark features to address security concerns.

## 2.3 Schema

## 2.3.1 Ultimate TODO Object

This is the root document object of the [Ultimate TODO document](#1.1-Ultimate-TODO-Document).

| Field Name | Type | Description |
| :-- | :-- | :-- |
| version | string | [Semantic Version Number](https://semver.org/spec/v2.0.0.html) denoting the Ultimate TODO document version. |
| tasks | [Task Object] | __REQUIRED__. Provides a list of all tasks created by a user. |

## 2.3.2 Task Object

This object defines a task.

| Field Name | Type | Description |
| :-- | :-- | :-- |
| id | string | REQUIRED. A unique identifier for the task. This id _SHALL_ be generated on creation of the task. |
| name | string | REQUIRED. The title of the task. |
| description | string | A short description of the task. [CommonMark syntax](https://spec.commonmark.org/) _MAY_ be used for rich text representation. |
| createdTime | Date | REQUIRED. A time-stamp denoting the creation of the task. |
| completed | boolean | A list of tasks required for completion of this task. String in the array _SHALL_ correspond to an existing task id. |
| completedTime | Date | A time-stamp denoting the completion of the task. |
| notes | string | Continuously updated meta-information about the task. [CommonMark syntax](https://spec.commonmark.org/) _MAY_ be used for rich text representation. |
| required | [string] | A list of tasks required for completion of this task. String in the array _SHALL_ correspond to an existing task id. |

