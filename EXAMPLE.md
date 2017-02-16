*****************LOGIC BLOCKS AND NOT GATES*****************

The basic idea behind how new logic blocks are made in joint.shapes.logic.js is through a form of inheritance, called extension.
For example, this is the code for creating a not gate

joint.shapes.logic.Not = joint.shapes.logic.Gate11.extend({

    defaults: _.defaultsDeep({

        type: 'logic.Not',
        attrs: { image: { 'xlink:href': 'data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiIHN0YW5kYWxvbmU9Im5vIj8+CjwhLS0gQ3JlYXRlZCB3aXRoIElua3NjYXBlIChodHRwOi8vd3d3Lmlua3NjYXBlLm9yZy8pIC0tPgo8c3ZnCiAgIHhtbG5zOmRjPSJodHRwOi8vcHVybC5vcmcvZGMvZWxlbWVudHMvMS4xLyIKICAgeG1sbnM6Y2M9Imh0dHA6Ly9jcmVhdGl2ZWNvbW1vbnMub3JnL25zIyIKICAgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIgogICB4bWxuczpzdmc9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIgogICB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciCiAgIHhtbG5zOnNvZGlwb2RpPSJodHRwOi8vc29kaXBvZGkuc291cmNlZm9yZ2UubmV0L0RURC9zb2RpcG9kaS0wLmR0ZCIKICAgeG1sbnM6aW5rc2NhcGU9Imh0dHA6Ly93d3cuaW5rc2NhcGUub3JnL25hbWVzcGFjZXMvaW5rc2NhcGUiCiAgIHdpZHRoPSIxMDAiCiAgIGhlaWdodD0iNTAiCiAgIGlkPSJzdmcyIgogICBzb2RpcG9kaTp2ZXJzaW9uPSIwLjMyIgogICBpbmtzY2FwZTp2ZXJzaW9uPSIwLjQ2IgogICB2ZXJzaW9uPSIxLjAiCiAgIHNvZGlwb2RpOmRvY25hbWU9Ik5PVCBBTlNJLnN2ZyIKICAgaW5rc2NhcGU6b3V0cHV0X2V4dGVuc2lvbj0ib3JnLmlua3NjYXBlLm91dHB1dC5zdmcuaW5rc2NhcGUiPgogIDxkZWZzCiAgICAgaWQ9ImRlZnM0Ij4KICAgIDxpbmtzY2FwZTpwZXJzcGVjdGl2ZQogICAgICAgc29kaXBvZGk6dHlwZT0iaW5rc2NhcGU6cGVyc3AzZCIKICAgICAgIGlua3NjYXBlOnZwX3g9IjAgOiAxNSA6IDEiCiAgICAgICBpbmtzY2FwZTp2cF95PSIwIDogMTAwMCA6IDAiCiAgICAgICBpbmtzY2FwZTp2cF96PSI1MCA6IDE1IDogMSIKICAgICAgIGlua3NjYXBlOnBlcnNwM2Qtb3JpZ2luPSIyNSA6IDEwIDogMSIKICAgICAgIGlkPSJwZXJzcGVjdGl2ZTI3MTQiIC8+CiAgICA8aW5rc2NhcGU6cGVyc3BlY3RpdmUKICAgICAgIHNvZGlwb2RpOnR5cGU9Imlua3NjYXBlOnBlcnNwM2QiCiAgICAgICBpbmtzY2FwZTp2cF94PSIwIDogMC41IDogMSIKICAgICAgIGlua3NjYXBlOnZwX3k9IjAgOiAxMDAwIDogMCIKICAgICAgIGlua3NjYXBlOnZwX3o9IjEgOiAwLjUgOiAxIgogICAgICAgaW5rc2NhcGU6cGVyc3AzZC1vcmlnaW49IjAuNSA6IDAuMzMzMzMzMzMgOiAxIgogICAgICAgaWQ9InBlcnNwZWN0aXZlMjgwNiIgLz4KICAgIDxpbmtzY2FwZTpwZXJzcGVjdGl2ZQogICAgICAgaWQ9InBlcnNwZWN0aXZlMjgxOSIKICAgICAgIGlua3NjYXBlOnBlcnNwM2Qtb3JpZ2luPSIzNzIuMDQ3MjQgOiAzNTAuNzg3MzkgOiAxIgogICAgICAgaW5rc2NhcGU6dnBfej0iNzQ0LjA5NDQ4IDogNTI2LjE4MTA5IDogMSIKICAgICAgIGlua3NjYXBlOnZwX3k9IjAgOiAxMDAwIDogMCIKICAgICAgIGlua3NjYXBlOnZwX3g9IjAgOiA1MjYuMTgxMDkgOiAxIgogICAgICAgc29kaXBvZGk6dHlwZT0iaW5rc2NhcGU6cGVyc3AzZCIgLz4KICAgIDxpbmtzY2FwZTpwZXJzcGVjdGl2ZQogICAgICAgaWQ9InBlcnNwZWN0aXZlMjc3NyIKICAgICAgIGlua3NjYXBlOnBlcnNwM2Qtb3JpZ2luPSI3NSA6IDQwIDogMSIKICAgICAgIGlua3NjYXBlOnZwX3o9IjE1MCA6IDYwIDogMSIKICAgICAgIGlua3NjYXBlOnZwX3k9IjAgOiAxMDAwIDogMCIKICAgICAgIGlua3NjYXBlOnZwX3g9IjAgOiA2MCA6IDEiCiAgICAgICBzb2RpcG9kaTp0eXBlPSJpbmtzY2FwZTpwZXJzcDNkIiAvPgogICAgPGlua3NjYXBlOnBlcnNwZWN0aXZlCiAgICAgICBpZD0icGVyc3BlY3RpdmUzMjc1IgogICAgICAgaW5rc2NhcGU6cGVyc3AzZC1vcmlnaW49IjUwIDogMzMuMzMzMzMzIDogMSIKICAgICAgIGlua3NjYXBlOnZwX3o9IjEwMCA6IDUwIDogMSIKICAgICAgIGlua3NjYXBlOnZwX3k9IjAgOiAxMDAwIDogMCIKICAgICAgIGlua3NjYXBlOnZwX3g9IjAgOiA1MCA6IDEiCiAgICAgICBzb2RpcG9kaTp0eXBlPSJpbmtzY2FwZTpwZXJzcDNkIiAvPgogICAgPGlua3NjYXBlOnBlcnNwZWN0aXZlCiAgICAgICBpZD0icGVyc3BlY3RpdmU1NTMzIgogICAgICAgaW5rc2NhcGU6cGVyc3AzZC1vcmlnaW49IjMyIDogMjEuMzMzMzMzIDogMSIKICAgICAgIGlua3NjYXBlOnZwX3o9IjY0IDogMzIgOiAxIgogICAgICAgaW5rc2NhcGU6dnBfeT0iMCA6IDEwMDAgOiAwIgogICAgICAgaW5rc2NhcGU6dnBfeD0iMCA6IDMyIDogMSIKICAgICAgIHNvZGlwb2RpOnR5cGU9Imlua3NjYXBlOnBlcnNwM2QiIC8+CiAgICA8aW5rc2NhcGU6cGVyc3BlY3RpdmUKICAgICAgIGlkPSJwZXJzcGVjdGl2ZTI1NTciCiAgICAgICBpbmtzY2FwZTpwZXJzcDNkLW9yaWdpbj0iMjUgOiAxNi42NjY2NjcgOiAxIgogICAgICAgaW5rc2NhcGU6dnBfej0iNTAgOiAyNSA6IDEiCiAgICAgICBpbmtzY2FwZTp2cF95PSIwIDogMTAwMCA6IDAiCiAgICAgICBpbmtzY2FwZTp2cF94PSIwIDogMjUgOiAxIgogICAgICAgc29kaXBvZGk6dHlwZT0iaW5rc2NhcGU6cGVyc3AzZCIgLz4KICA8L2RlZnM+CiAgPHNvZGlwb2RpOm5hbWVkdmlldwogICAgIGlkPSJiYXNlIgogICAgIHBhZ2Vjb2xvcj0iI2ZmZmZmZiIKICAgICBib3JkZXJjb2xvcj0iIzY2NjY2NiIKICAgICBib3JkZXJvcGFjaXR5PSIxLjAiCiAgICAgaW5rc2NhcGU6cGFnZW9wYWNpdHk9IjAuMCIKICAgICBpbmtzY2FwZTpwYWdlc2hhZG93PSIyIgogICAgIGlua3NjYXBlOnpvb209IjgiCiAgICAgaW5rc2NhcGU6Y3g9Ijg0LjY4NTM1MiIKICAgICBpbmtzY2FwZTpjeT0iMTUuMjg4NjI4IgogICAgIGlua3NjYXBlOmRvY3VtZW50LXVuaXRzPSJweCIKICAgICBpbmtzY2FwZTpjdXJyZW50LWxheWVyPSJsYXllcjEiCiAgICAgc2hvd2dyaWQ9InRydWUiCiAgICAgaW5rc2NhcGU6Z3JpZC1iYm94PSJ0cnVlIgogICAgIGlua3NjYXBlOmdyaWQtcG9pbnRzPSJ0cnVlIgogICAgIGdyaWR0b2xlcmFuY2U9IjEwMDAwIgogICAgIGlua3NjYXBlOndpbmRvdy13aWR0aD0iMTM5OSIKICAgICBpbmtzY2FwZTp3aW5kb3ctaGVpZ2h0PSI4NzQiCiAgICAgaW5rc2NhcGU6d2luZG93LXg9IjMzIgogICAgIGlua3NjYXBlOndpbmRvdy15PSIwIgogICAgIGlua3NjYXBlOnNuYXAtYmJveD0idHJ1ZSI+CiAgICA8aW5rc2NhcGU6Z3JpZAogICAgICAgaWQ9IkdyaWRGcm9tUHJlMDQ2U2V0dGluZ3MiCiAgICAgICB0eXBlPSJ4eWdyaWQiCiAgICAgICBvcmlnaW54PSIwcHgiCiAgICAgICBvcmlnaW55PSIwcHgiCiAgICAgICBzcGFjaW5neD0iMXB4IgogICAgICAgc3BhY2luZ3k9IjFweCIKICAgICAgIGNvbG9yPSIjMDAwMGZmIgogICAgICAgZW1wY29sb3I9IiMwMDAwZmYiCiAgICAgICBvcGFjaXR5PSIwLjIiCiAgICAgICBlbXBvcGFjaXR5PSIwLjQiCiAgICAgICBlbXBzcGFjaW5nPSI1IgogICAgICAgdmlzaWJsZT0idHJ1ZSIKICAgICAgIGVuYWJsZWQ9InRydWUiIC8+CiAgPC9zb2RpcG9kaTpuYW1lZHZpZXc+CiAgPG1ldGFkYXRhCiAgICAgaWQ9Im1ldGFkYXRhNyI+CiAgICA8cmRmOlJERj4KICAgICAgPGNjOldvcmsKICAgICAgICAgcmRmOmFib3V0PSIiPgogICAgICAgIDxkYzpmb3JtYXQ+aW1hZ2Uvc3ZnK3htbDwvZGM6Zm9ybWF0PgogICAgICAgIDxkYzp0eXBlCiAgICAgICAgICAgcmRmOnJlc291cmNlPSJodHRwOi8vcHVybC5vcmcvZGMvZGNtaXR5cGUvU3RpbGxJbWFnZSIgLz4KICAgICAgPC9jYzpXb3JrPgogICAgPC9yZGY6UkRGPgogIDwvbWV0YWRhdGE+CiAgPGcKICAgICBpbmtzY2FwZTpsYWJlbD0iTGF5ZXIgMSIKICAgICBpbmtzY2FwZTpncm91cG1vZGU9ImxheWVyIgogICAgIGlkPSJsYXllcjEiPgogICAgPHBhdGgKICAgICAgIHN0eWxlPSJmaWxsOm5vbmU7c3Ryb2tlOiMwMDAwMDA7c3Ryb2tlLXdpZHRoOjEuOTk5OTk5ODg7c3Ryb2tlLWxpbmVjYXA6YnV0dDtzdHJva2UtbGluZWpvaW46bWl0ZXI7c3Ryb2tlLW9wYWNpdHk6MSIKICAgICAgIGQ9Ik0gNzkuMTU2OTEsMjUgTCA5NSwyNSIKICAgICAgIGlkPSJwYXRoMzA1OSIKICAgICAgIHNvZGlwb2RpOm5vZGV0eXBlcz0iY2MiIC8+CiAgICA8cGF0aAogICAgICAgc3R5bGU9ImZpbGw6bm9uZTtzdHJva2U6IzAwMDAwMDtzdHJva2Utd2lkdGg6MjtzdHJva2UtbGluZWNhcDpidXR0O3N0cm9rZS1saW5lam9pbjptaXRlcjtzdHJva2Utb3BhY2l0eToxIgogICAgICAgZD0iTSAyOS4wNDM0NzgsMjUgTCA1LjA0MzQ3ODEsMjUiCiAgICAgICBpZD0icGF0aDMwNjEiIC8+CiAgICA8cGF0aAogICAgICAgc3R5bGU9ImZpbGw6IzAwMDAwMDtmaWxsLW9wYWNpdHk6MTtzdHJva2U6bm9uZTtzdHJva2Utd2lkdGg6MztzdHJva2UtbGluZWpvaW46bWl0ZXI7bWFya2VyOm5vbmU7c3Ryb2tlLW9wYWNpdHk6MTt2aXNpYmlsaXR5OnZpc2libGU7ZGlzcGxheTppbmxpbmU7b3ZlcmZsb3c6dmlzaWJsZTtlbmFibGUtYmFja2dyb3VuZDphY2N1bXVsYXRlIgogICAgICAgZD0iTSAyOC45Njg3NSwyLjU5Mzc1IEwgMjguOTY4NzUsNSBMIDI4Ljk2ODc1LDQ1IEwgMjguOTY4NzUsNDcuNDA2MjUgTCAzMS4xMjUsNDYuMzQzNzUgTCA3Mi4xNTYyNSwyNi4zNDM3NSBMIDcyLjE1NjI1LDIzLjY1NjI1IEwgMzEuMTI1LDMuNjU2MjUgTCAyOC45Njg3NSwyLjU5Mzc1IHogTSAzMS45Njg3NSw3LjQwNjI1IEwgNjguMDkzNzUsMjUgTCAzMS45Njg3NSw0Mi41OTM3NSBMIDMxLjk2ODc1LDcuNDA2MjUgeiIKICAgICAgIGlkPSJwYXRoMjYzOCIKICAgICAgIHNvZGlwb2RpOm5vZGV0eXBlcz0iY2NjY2NjY2NjY2NjYyIgLz4KICAgIDxwYXRoCiAgICAgICBzb2RpcG9kaTp0eXBlPSJhcmMiCiAgICAgICBzdHlsZT0iZmlsbDpub25lO2ZpbGwtb3BhY2l0eToxO3N0cm9rZTojMDAwMDAwO3N0cm9rZS13aWR0aDozO3N0cm9rZS1saW5lam9pbjptaXRlcjttYXJrZXI6bm9uZTtzdHJva2Utb3BhY2l0eToxO3Zpc2liaWxpdHk6dmlzaWJsZTtkaXNwbGF5OmlubGluZTtvdmVyZmxvdzp2aXNpYmxlO2VuYWJsZS1iYWNrZ3JvdW5kOmFjY3VtdWxhdGUiCiAgICAgICBpZD0icGF0aDI2NzEiCiAgICAgICBzb2RpcG9kaTpjeD0iNzYiCiAgICAgICBzb2RpcG9kaTpjeT0iMjUiCiAgICAgICBzb2RpcG9kaTpyeD0iNCIKICAgICAgIHNvZGlwb2RpOnJ5PSI0IgogICAgICAgZD0iTSA4MCwyNSBBIDQsNCAwIDEgMSA3MiwyNSBBIDQsNCAwIDEgMSA4MCwyNSB6IgogICAgICAgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoLTEsMCkiIC8+CiAgPC9nPgo8L3N2Zz4K' }}

    }, joint.shapes.logic.Gate11.prototype.defaults),

    operation: function(input) {
        return !input;
    }

});

joint.shapes.logic is a bag of objects. By saying joint.shapes.logic.Not = blahblahblah... we are adding an object
called Not to joint.shapes.logic. 

This Not object is an extension of the Gate11 object, which is a generic block for logic gates with one input and one output.

Creating logic gates with an arbitrary number of inputs and outputs is possible by creating the appropriate Gate object first,
similarly to how Gate11 and Gate21 are created.

Within the extend() function there are some default values specified as well as an operation.
The default values include the type of gate (which should be the last two specifiers after joint.shapes)
as well as the attrs attribute, which is where the SVG for the gate is placed. This is a base64 encoded SVG,
there are online applications for converting an SVG into base64 for use in this code, or explicit links to SVG files
can be used as well.

joint.shapes.logic.Gate11.prototype.defaults is used to specify the rest of the defaults for this Not gate.

Finally, there is an operation attribute, this is where the actual function which the gate computes is performed.
In general we should expect the input to be any integers, though we may later consider only non-negative inputs, since hex
encoded text is always a positive number.


*****************ADDITION and GATE21*****************

Here is an example of addition, which is an extension of Gate21:


joint.shapes.logic.Sum = joint.shapes.logic.Gate21.extend({

    defaults: _.defaultsDeep({

    type: 'logic.Sum',
		attrs: { image: { 'xlink:href': 'data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiIHN0YW5kYWxvbmU9Im5vIj8+PHN2ZyAgIHhtbG5zOmRjPSJodHRwOi8vcHVybC5vcmcvZGMvZWxlbWVudHMvMS4xLyIgICB4bWxuczpjYz0iaHR0cDovL2NyZWF0aXZlY29tbW9ucy5vcmcvbnMjIiAgIHhtbG5zOnJkZj0iaHR0cDovL3d3dy53My5vcmcvMTk5OS8wMi8yMi1yZGYtc3ludGF4LW5zIyIgICB4bWxuczpzdmc9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiAgIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgICB4bWxuczpzb2RpcG9kaT0iaHR0cDovL3NvZGlwb2RpLnNvdXJjZWZvcmdlLm5ldC9EVEQvc29kaXBvZGktMC5kdGQiICAgeG1sbnM6aW5rc2NhcGU9Imh0dHA6Ly93d3cuaW5rc2NhcGUub3JnL25hbWVzcGFjZXMvaW5rc2NhcGUiICAgd2lkdGg9Ijk1LjA2NzUzNW1tIiAgIGhlaWdodD0iMzYuMjg1NzEzbW0iICAgdmlld0JveD0iMCAwIDk1LjA2NzUzNSAzNi4yODU3MTMiICAgdmVyc2lvbj0iMS4xIiAgIGlkPSJzdmc4IiAgIGlua3NjYXBlOnZlcnNpb249IjAuOTIuMCByMTUyOTkiICAgc29kaXBvZGk6ZG9jbmFtZT0iYWRkLnN2ZyI+ICA8ZGVmcyAgICAgaWQ9ImRlZnMyIiAvPiAgPHNvZGlwb2RpOm5hbWVkdmlldyAgICAgaWQ9ImJhc2UiICAgICBwYWdlY29sb3I9IiNmZmZmZmYiICAgICBib3JkZXJjb2xvcj0iIzY2NjY2NiIgICAgIGJvcmRlcm9wYWNpdHk9IjEuMCIgICAgIGlua3NjYXBlOnBhZ2VvcGFjaXR5PSIwLjAiICAgICBpbmtzY2FwZTpwYWdlc2hhZG93PSIyIiAgICAgaW5rc2NhcGU6em9vbT0iMS4wMzAyMjQ2IiAgICAgaW5rc2NhcGU6Y3g9Ii0yNTMuNjExNzQiICAgICBpbmtzY2FwZTpjeT0iMTE1LjIwMzgxIiAgICAgaW5rc2NhcGU6ZG9jdW1lbnQtdW5pdHM9Im1tIiAgICAgaW5rc2NhcGU6Y3VycmVudC1sYXllcj0ibGF5ZXIxIiAgICAgc2hvd2dyaWQ9ImZhbHNlIiAgICAgaW5rc2NhcGU6d2luZG93LXdpZHRoPSIxOTIwIiAgICAgaW5rc2NhcGU6d2luZG93LWhlaWdodD0iMTAxNyIgICAgIGlua3NjYXBlOndpbmRvdy14PSItOCIgICAgIGlua3NjYXBlOndpbmRvdy15PSItOCIgICAgIGlua3NjYXBlOndpbmRvdy1tYXhpbWl6ZWQ9IjEiIC8+ICA8bWV0YWRhdGEgICAgIGlkPSJtZXRhZGF0YTUiPiAgICA8cmRmOlJERj4gICAgICA8Y2M6V29yayAgICAgICAgIHJkZjphYm91dD0iIj4gICAgICAgIDxkYzpmb3JtYXQ+aW1hZ2Uvc3ZnK3htbDwvZGM6Zm9ybWF0PiAgICAgICAgPGRjOnR5cGUgICAgICAgICAgIHJkZjpyZXNvdXJjZT0iaHR0cDovL3B1cmwub3JnL2RjL2RjbWl0eXBlL1N0aWxsSW1hZ2UiIC8+ICAgICAgICA8ZGM6dGl0bGU+PC9kYzp0aXRsZT4gICAgICA8L2NjOldvcms+ICAgIDwvcmRmOlJERj4gIDwvbWV0YWRhdGE+ICA8ZyAgICAgaW5rc2NhcGU6bGFiZWw9IkxheWVyIDEiICAgICBpbmtzY2FwZTpncm91cG1vZGU9ImxheWVyIiAgICAgaWQ9ImxheWVyMSIgICAgIHRyYW5zZm9ybT0idHJhbnNsYXRlKC0wLjM2MzE5OTU2LC0wLjA4ODAzNDIzKSI+ICAgIDxyZWN0ICAgICAgIGlkPSJyZWN0MzY4MCIgICAgICAgd2lkdGg9IjQ0LjYwMTE4OSIgICAgICAgaGVpZ2h0PSIzNi4yODU3MTMiICAgICAgIHg9IjI1LjYzODk4OCIgICAgICAgeT0iMC4wODgwMzQyMzUiICAgICAgIHN0eWxlPSJzdHJva2Utd2lkdGg6MC4yNjQ1ODMzMiIgLz4gICAgPHRleHQgICAgICAgeG1sOnNwYWNlPSJwcmVzZXJ2ZSIgICAgICAgc3R5bGU9ImZvbnQtc3R5bGU6bm9ybWFsO2ZvbnQtd2VpZ2h0Om5vcm1hbDtmb250LXNpemU6MzIuOTU2NzEwODJweDtsaW5lLWhlaWdodDoyMC41OTc5NDQyNnB4O2ZvbnQtZmFtaWx5OnNhbnMtc2VyaWY7bGV0dGVyLXNwYWNpbmc6MHB4O3dvcmQtc3BhY2luZzowcHg7ZmlsbDojMDAwMDAwO2ZpbGwtb3BhY2l0eToxO3N0cm9rZTpub25lO3N0cm9rZS13aWR0aDowLjgyMzkxNzgxIiAgICAgICB4PSIzMy44NzI3IiAgICAgICB5PSIzMC41NTk1NjUiICAgICAgIGlkPSJ0ZXh0MzY4NCIgICAgICAgdHJhbnNmb3JtPSJzY2FsZSgxLjA4ODA5MDMsMC45MTkwNDEzNykiPjx0c3BhbiAgICAgICAgIHNvZGlwb2RpOnJvbGU9ImxpbmUiICAgICAgICAgaWQ9InRzcGFuMzY4MiIgICAgICAgICB4PSIzMy44NzI3IiAgICAgICAgIHk9IjMwLjU1OTU2NSIgICAgICAgICBzdHlsZT0iZmlsbDojZmZmZmZmO3N0cm9rZS13aWR0aDowLjgyMzkxNzgxIj4rPC90c3Bhbj48L3RleHQ+ICAgIDxyZWN0ICAgICAgIHN0eWxlPSJmaWxsOiM5OTk5OTk7c3Ryb2tlLXdpZHRoOjAuMTQ1Njc1MDMiICAgICAgIGlkPSJyZWN0MzY5MCIgICAgICAgd2lkdGg9IjI1LjI0MjM4NCIgICAgICAgaGVpZ2h0PSIxLjg5OTI0MDUiICAgICAgIHg9IjAuMzYzMTk5NTYiICAgICAgIHk9IjQuOTg0Njg1NCIgLz4gICAgPHJlY3QgICAgICAgc3R5bGU9ImZpbGw6Izk5OTk5OTtzdHJva2Utd2lkdGg6MC4xNDU2NzUwMiIgICAgICAgaWQ9InJlY3QzNjkwLTEiICAgICAgIHdpZHRoPSIyNS4yNDIzODQiICAgICAgIGhlaWdodD0iMS44OTkyNCIgICAgICAgeD0iMC4zNjMyMDA1MiIgICAgICAgeT0iMzIuNDYxOTE4IiAvPiAgICA8cmVjdCAgICAgICBzdHlsZT0iZmlsbDojOTk5OTk5O3N0cm9rZS13aWR0aDowLjEyNDQyNjg0IiAgICAgICBpZD0icmVjdDM2OTAtOSIgICAgICAgd2lkdGg9IjI1LjI0MjM4NCIgICAgICAgaGVpZ2h0PSIxLjM4NTYwMDEiICAgICAgIHg9IjcwLjE4ODM1NCIgICAgICAgeT0iMTcuNjY0MTk0IiAvPiAgPC9nPjwvc3ZnPg=='
		}}
    }, joint.shapes.logic.Gate21.prototype.defaults),

    operation: function(input1, input2) {
		return input1 + input2;
    }

});

As you can see, the code is almost identical to that for the Not gate, but the operation now takes two inputs.



The code for Gate21 is as follows:

joint.shapes.logic.Gate21 = joint.shapes.logic.Gate.extend({

    markup: '<g class="rotatable"><g class="scalable"><image class="body"/></g><circle class="input input1"/><circle  class="input input2"/><circle class="output"/></g>',

    defaults: _.defaultsDeep({

        type: 'logic.Gate21',
        attrs: {
            '.input1': { ref: '.body', 'ref-x': -2, 'ref-y': 0.3, magnet: 'passive', port: 'in1' },
            '.input2': { ref: '.body', 'ref-x': -2, 'ref-y': 0.7, magnet: 'passive', port: 'in2' },
            '.output': { ref: '.body', 'ref-dx': 2, 'ref-y': 0.5, magnet: true, port: 'out' }
        }

    }, joint.shapes.logic.Gate.prototype.defaults)

});

Which is a bit more complex, but still fairly straightforward. As you can see, the markup has to be specified, which
corresponds to the HTML generated. This markup will need to be extended according to the number of inputs and outputs.
Further, we can see that the inputs and outputs are specified here by giving them names and attributes in the attrs section.
First the position of the ports are specified using ref, ref-x, ref-dx, ref-y and ref-dy (not shown here).
Next, the 'magnet type' is specified. This specifies whether the port is input ('passive') or output (true).
Lastly, the ports are given names.

If you take a look at the code for Sum, you can see that the operation takes two inputs input1 and input2. These are exactly
the inputs which are created in the Gate21 code. Now take a look at Gate11:

joint.shapes.logic.Gate11 = joint.shapes.logic.Gate.extend({

    markup: '<g class="rotatable"><g class="scalable"><image class="body"/></g><circle class="input"/><circle class="output"/></g>',

    defaults: _.defaultsDeep({

        type: 'logic.Gate11',
        attrs: {
            '.input': { ref: '.body', 'ref-x': -2, 'ref-y': 0.5, magnet: 'passive', port: 'in' },
            '.output': { ref: '.body', 'ref-dx': 2, 'ref-y': 0.5, magnet: true, port: 'out' }
        }

    }, joint.shapes.logic.Gate.prototype.defaults)
});

There is only one input, called input. This is exactly the input that the operation for the Not gate is using. 



*****************OKAY... NOW HOW THE HECK DO I INSTANTIATE THESE IN HTML?*****************

Good question. Take a look near the bottom of the logic.html file and you'll see this code

var gates = {
	four1: new joint.shapes.logic.Four({ position: { x: 100, y: 90 }}),
	four2: new joint.shapes.logic.Four({ position: { x: 100, y: 220 }}),
	sig: new joint.shapes.logic.Signal({ position: { x: 440, y: 155 }}),
	sum: new joint.shapes.logic.Sum({ position: { x: 240, y: 150 }}),
	el1: new joint.shapes.html.Element({
        position: { x: 550, y: 55 },
        size: { width: 120, height: 60 }
    })
};

This is where the gates are specified. The gates must be given a name (e.g. four1, four2, sig, etc.) and then a
new logic gate is instantiated using our previously created logic block code. There is no need to make a constructor or anything,
just specify the structure of the logic block in joint.shapes.logic.js and you'll be good to go. The only thing the constructor
normally takes is an intial position of the logic gate on the canvas.

Now, there's one more catch. If you look above, you'll see that not every logic block is contained in joint.shapes.logic.
The last block, el1 (which is our numeric input block), is of type joint.shapes.html. This is because this block is fancier
than a standard logic block, it has an active html element built into it which defines its value. The code for this block has been
placed into the top of the logic.html file for now, but should be separated eventually. And no, I didn't write all of that scary code
myself, I've just been making modifications to pre-existing code examples.


That should be a decent amount of information, and hopefully enough to start crafting your own logic blocks!
