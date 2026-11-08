### My name is Jeff

I work on cloud platforms and the security built into them. I'd rather build the secure path into the platform than review every change by hand. Engineers ship without waiting on me, and the controls still hold.

My side projects follow the same rules, which is much more than a one-person AWS org needs.

**How I build**

| Rule | How it holds |
|---|---|
| **Every change goes through a PR** | CI applies only what that PR planned. |
| **No long-lived cloud keys in CI** | Each workflow assumes its own OIDC role. Plan, apply and drift are separate roles, so a stolen token gets one job's permissions. |
| **Drift fails loudly** | A daily check fails when the cloud stops matching the code. A dead-man's switch emails me if the check stops running. |
| **Guardrails go to staging first** | I read CloudTrail for what each one denies before it goes further. |
| **Admin sign-in needs hardware** | A YubiKey or Okta FastPass, never a synced passkey. The policy is imported read-only, so any loosening shows up as drift. |
| **The easy path ships with its controls** | My scheduled-job module includes code signing, a dead-letter queue and alarms by default. |

**What I'm working on**

| Project | What it is | Status |
|---|---|---|
| **AWS organization** | OpenTofu. Everything above runs here. It emails me on any root sign-in, and the same repo manages Okta. | Private, public soon with its decision records |
| **entramations** | An MIT-licensed Python library of Microsoft Entra ID automations. Each one runs against any tenant from config. I build one only when Microsoft's features and existing community tools don't already do the job. | Private, public soon |
