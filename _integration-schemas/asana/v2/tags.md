---
tap: "asana"
version: "2"
key: "tag"

name: "tags"
doc-link: "https://asana.com/developers/api-reference/tags"
singer-schema: "https://github.com/singer-io/tap-asana/blob/master/tap_asana/schemas/tags.json"
description: |
  The `{{ table.name }}` table contains info about the tags in your {{ integration.display_name }} account. A tag is a label that can be attached to any task in Asana.

replication-method: "Key-based Incremental"

attributes:
  - name: "gid"
    type: "string"
    primary-key: true
    description: "The tag GID."
    #foreign-key-id: "tag-id"

  - name: "created_at"
    type: "date-time"
    replication-key: true
    description: "The time the tag was created."

  - name: "color"
    type: "string"
    description: |
      The color of the tag. Possible values are:

      - `dark-pink`
      - `dark-green` 
      - `dark-blue`
      - `dark-red`
      - `dark-teal` 
      - `dark-brown` 
      - `dark-orange` 
      - `dark-purple`
      - `dark-warm-gray` 
      - `light-pink`
      - `light-green` 
      - `light-blue`
      - `light-red`
      - `light-teal` 
      - `light-yellow` 
      - `light-orange`
      - `light-purple`
      - `light-warm-gray`

  - name: "followers"
    type: "array"
    description: "A list of users following the tag."
    subattributes:
      - name: "gid"
        type: "string"
        description: "The follower's GID."
        foreign-key-id: "user-id"

      - name: "resource_type"
        type: "string"
        description: "This will be `user`."

  - name: "name"
    type: "string"
    description: "The name of the tag."

  - name: "notes"
    type: "string"
    description: "Any notes associated with the tag."

  - name: "workspace"
    type: "object"
    description: "Details about the workspace or organization the tag is associated with."
    subattributes:
      - name: "gid"
        type: "string"
        description: "The workspace's GID."
        foreign-key-id: "workspace-id"

      - name: "resource_type"
        type: "string"
        description: "This will be `workspace`."
---