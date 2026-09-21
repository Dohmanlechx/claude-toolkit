# Domains - what you hunt for

Read the target through all four lenses. Every hit becomes a private
question, ordered by severity (credential exposure and broken transport
security outrank style-level findings). On a clean target, do not invent
findings: ask the few questions the artifact genuinely raises (data
flows, assumptions, deployment context) and let the interview be short.

## Lens 1: general cyber security

Injection of every kind (shell, SQL, path, header, deserialization),
authz gaps, missing validation at trust boundaries, unsafe defaults,
race conditions on security decisions, secrets in logs or error
messages, dependency risks visible in the change.

## Lens 2: network security

Cleartext protocols (`http://`, ws, ftp, smtp without TLS), disabled or
weakened TLS verification (trust-all managers, hostname verifiers that
accept everything, pinned-then-disabled), open or wildcard listeners,
overly broad allowlists/CORS, hardcoded endpoints, admin surfaces
reachable from user paths.

## Lens 3: secret handling

EVERY reference to a secret - key, token, password, certificate,
connection string - triggers the standing checklist. One question per
item, per secret:

1. Where is it stored? (vault, env, CI secret, plaintext in repo)
2. How does it get there? (provisioning path, who puts it in place)
3. Who can read it? (people, services, build systems)
4. Has it ever touched git history? (and if so: was it rotated and the
   history purged?)

A secret that fails item 4 is a live incident, not a cleanup ticket.

## Lens 4: AI-generated-looking code

Tells: uncanny uniform comment cadence (step-numbered narration of
trivial lines), doc comments restating the signature in prose, dead
generality (parameters, branches, or configurability nothing uses),
over-symmetric error handling, tutorial phrasing ("This function is
responsible for...").

When a passage looks strongly AI-generated, make the author explain
what it does and why it is written that way - the point is to verify
the author understands their own code, not to shame the tool. Judge
the explanation like any other answer: vague means follow up.
