Here's a markdown summary of the page:

---

# Supabase OAuth 2.1 Server — Overview

Supabase Auth can act as an **OAuth 2.1 and OpenID Connect (OIDC) identity provider**, letting other apps use your Supabase project for authentication (like "Sign in with [Your App]").

## Use Cases

- **Developer platforms & marketplaces** — Let third-party developers build integrations with "Sign in with [Your App]" flows, gated by Row Level Security (RLS).
- **AI agents & automation** — Authenticate LLM tools and MCP servers that need access to user data via the Model Context Protocol (MCP).
- **Mobile & desktop apps** — Issue OAuth tokens to first-party clients; all tokens respect existing RLS policies and Custom Access Token Hooks.
- **Enterprise SSO** — Provide OIDC-compliant identity federation across multiple services.

## How It Works (Authorization Code Flow + PKCE)

1. Third-party app redirects user to your authorization endpoint.
2. Supabase Auth validates the request and shows your custom auth UI.
3. User authenticates (any enabled method) and approves access.
4. Supabase Auth issues an **authorization code**.
5. App exchanges the code for **access + refresh tokens**.
6. App uses the access token to make authenticated API requests.

> Access tokens are standard Supabase JWTs containing `user_id`, `role`, and `client_id` claims.

## Supported Standards

| Standard | Details |
|---|---|
| OAuth 2.1 | Mandatory PKCE |
| OpenID Connect | ID tokens, UserInfo endpoint, OIDC discovery |
| Standard scopes | `openid`, `email`, `profile`, `phone` |
| Dynamic client registration | Auto-registration for MCP clients |
| JWKS endpoint | Public keys for token validation |

## Integration with Existing Supabase Auth

- Works with all sign-in methods (password, magic link, social, MFA, phone)
- **Custom Access Token Hooks** can customize claims per client
- **Row Level Security** uses the `client_id` claim for fine-grained access control

## Sub-guides

- [Getting Started](https://supabase.com/docs/guides/auth/oauth-server/getting-started) — Enable OAuth 2.1 and register your first client
- [OAuth Flows](https://supabase.com/docs/guides/auth/oauth-server/oauth-flows) — Authorization code & refresh token flows
- [MCP Authentication](https://supabase.com/docs/guides/auth/oauth-server/mcp-authentication) — Authenticate AI agents via MCP
- [Token Security & RLS](https://supabase.com/docs/guides/auth/oauth-server/token-security) — Control data access with RLS policies