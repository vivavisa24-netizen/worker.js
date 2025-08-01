export default {
  async fetch(request, env, ctx) {
    const response = await fetch(request);
    const newHeaders = new Headers(response.headers);
    newHeaders.delete("Content-Security-Policy");
    return new Response(response.body, {
      status: response.status,
      statusText: response.statusText,
      headers: newHeaders
    });
  }
}
name = "remove-csp-worker"
main = "worker.js"
compatibility_date = "2024-08-01"
