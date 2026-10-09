# Designs

One folder per product, and inside it one folder per variant.

```
designs/
  one/              OOMWOO One robot vacuum
    stock/          the standard OOMWOO One: Fusion 360 sources, STEP exports
    agentic/        AI-generated design experiments, kept for reference - not the design
```

## Why variants

A mod rarely touches one part. A top plate that gives a cat a ride, say, changes the
enclosure, the bumper and the way they mount to the base. A variant folder holds the
**whole** modified design, so anyone can open it and build it in one go instead of
piecing changed parts together from several places.

## Adding a variant

1. Copy `stock/` (or the variant you are starting from) to a new folder named after
   your mod, for example `designs/one/cat-rider/`.
2. Change what you need.
3. Add a `README.md` saying what changed and why, with a picture if you have one.
4. Open a pull request.

Off-the-shelf parts - motors, sensors, brushes, the 3D-scanned STEP models - live in
[`lib/`](../lib), shared by every product and variant.
