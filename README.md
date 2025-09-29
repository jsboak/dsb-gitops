# dsb-gitops

Flux configuration for the `perf-lab-use1` cluster. It deploys the DeathStarBench suites from `jsboak/DeathStarBench` for load and autoscaling experiments.

## Layout

- `clusters/perf-lab-use1`: Flux entry points, one Kustomization per component
- `apps/sources`: the pinned DeathStarBench source
- `apps/perf/<suite>`: Helm releases and extras for each suite
- `apps/perf/loadtest`: the nightly wrk2 run against the social network
- `infrastructure/perf`: cluster add-ons (AWS Load Balancer Controller)

The cluster itself comes from `jsboak/dsb-infra`. There is no dev cluster yet.

## Bumping DeathStarBench

Edit `ref.commit` in `apps/sources/deathstarbench.yaml`, open a PR, and watch the `social-network` release after merge. The images are mirrored to ECR under `deathstarbench/`.
