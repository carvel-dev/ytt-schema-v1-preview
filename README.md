# ytt-schema-v1-preview


## Setup

- create an alias for `ytt` that enables schema features:
  ```console
  $ alias ytts='ytt --enable-experiment-schema'  
  ```
  This removes the need to keep specifying this flag.

## Notes

- for this session, we'll use the `--data-values-file` mechanism for providing data values to `ytt` invocations. It is our intent to make this mechanism the _primary_ way that data values are supplied.
