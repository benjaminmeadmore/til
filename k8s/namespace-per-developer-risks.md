# What are the risks associated with a one-developer-per-namespace, one-cluster-per-org, setup ? 

Multi-tenancy in K8s is hard. Having one org-per-cluster involves several risks because of how K8s stacks keep all resources configuration-based 



Resource exhaustion - Without proper `ResourceQuotas` and `LimitRanges`, a developer can accidentally (or intentionally) consume all cluster resources. One misconfigured deployment doing `replicas: 1000` or a memory leak can starve other namespaces. Always set hard limits on CPU, memory, and pod counts per namespace.

  Privilege escalation - If RBAC isn't locked down properly, developers might be able to create roles/rolebindings that grant themselves more permissions than intended. Even within a
  namespace, they could potentially escalate to cluster-admin if you're not careful with verbs like escalate and bind.

  Network policies - By default, pods can talk to any other pod in any namespace. Without NetworkPolicies, a compromised or malicious pod in one developer's namespace could access
  services in another namespace, including things like internal databases or admin tools. You need to explicitly deny cross-namespace traffic and only whitelist what's necessary.

  Secrets access - Developers with namespace access can read all secrets in that namespace. If you're storing sensitive credentials (DB passwords, API keys) as secrets, they're base64
   encoded but not encrypted at rest by default. Consider using external secret management (Vault, AWS Secrets Manager) or enabling encryption at rest.

  Image security - Developers can pull and run arbitrary container images unless you enforce admission control. They could run outdated images with known CVEs, cryptocurrency miners,
  or images from untrusted registries. Use tools like OPA Gatekeeper or Kyverno to enforce image policies.

  Cost visibility - Each namespace becomes a potential cost center. Without proper monitoring and chargeback mechanisms, you lose visibility into who's burning through your cloud
  budget. Tag everything and use cost allocation tools.

Some orgs go full "cluster-per-team" instead because the isolation guarantees are stronger, though that has its own operational overhead.