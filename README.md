# portfolio-aws

Shared helpers for portfolio demos that call **real** AWS services.

- **No API keys in git** — use IAM roles (Lambda) or your local AWS profile.
- **Secrets Manager** — optional JSON secret referenced by `PORTFOLIO_SECRET_ARN`.

## Local install

```bash
pip install -e /Users/scottleduc/Projects/portfolio/libs/portfolio_aws
```

## Smoke test (after CDK deploy)

```bash
export PORTFOLIO_SECRET_ARN=arn:aws:secretsmanager:...
export AWS_REGION=us-east-1
python -c "
from portfolio_aws import BedrockConverse
r = BedrockConverse().complete('Reply with exactly: portfolio-aws-ok')
print(r.text[:200], 'tokens=', r.total_tokens)
"
```
