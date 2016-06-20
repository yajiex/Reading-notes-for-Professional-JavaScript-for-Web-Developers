# 2 JavaScript in HTML
* A `<script>` element using the `src` attribute should not include additional JavaScript code between the `<script>` and `</script>` tags. If both are provided, the script file is downloaded and executed while the inline code is ignored.
* The `defer` attribute is supported only for external script files, and scripts will be executed in the order in which they appear, before `DOMContentLoaded`.
* The `async` attribute applies only to external scripts and signals the browser to begin downloading the file immediately. But scripts marked as `async` are not guaranteed to execute in the order in which they are specified. Asynchronous scripts are guaranteed to execute before the page's `load` event and may execute before or after `DOMContentLoaded`.
* 