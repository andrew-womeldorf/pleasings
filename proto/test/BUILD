# Example usage of grpc_gateway_library rules.
subinclude('//proto:grpc_gateway')

grpc_gateway_library(
    name = 'kitten',
    srcs = ['kitten.proto'],
    # Limit language bindings so we don't have to have the other language plugins
    # installed on CI servers.
    languages = [
        'go',
        'py',
    ],
)

grpc_swagger_library(
    name = 'kitten_swagger',
    srcs = [':kitten'],
)

go_binary(
    name = 'kitten_gateway',
    srcs = ['gateway_main.go'],
    deps = [
        ':kitten',
        '//third_party/go:go-flags',
        '//third_party/go:grpc',
        '//third_party/go:grpc-gateway',
    ],
)

python_binary(
    name = 'kitten_server',
    main = 'server_main.py',
    deps = [
        ':kitten',
        '//third_party/python:grpc',
    ],
)
