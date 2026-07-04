---
navigation:
  title: Matter Manipulator Improvements
  parent: misc.md
  icon: matter-manipulator:itemMatterManipulator3
categories:
    - Features & Tweaks
author: Skorched
date: 2026-05-16
---

# Matter Manipulator Improvements
The <Color id="GREEN">Matter Manipulator</Color> <ItemImage id="matter-manipulator:itemMatterManipulator3" /> includes advanced capabilities for large-scale building.

# Advanced Copy Options (Smart Copy)
The Copy/Paste radial menu includes an <Color id="BLUE">__Advanced Options__</Color> sub-menu with three toggles:
- __Link to External Hubs (MKII+)__: When copying wireless connectors linked to a hub _outside_ of the copied region, pasted connectors will remain linked to that hub!
- __Auto-P2P Interfaces (MKII+)__: Replaces ME interfaces with P2P ME Interface tunnels. The source will receive an "input-side" tunnel, and the pasted version will get the "output-side" tunnel, with frequencies automatically matches. Patterns will remain at the source, so you can replicate processing set-ups that all route to that single set of patterns! (This also works with Fluid P2P Interface tunnels)
- __Auto-Proxy CRIBs (MKIII)__: Replaces <Color id="RED">Crafting Input Buses</Color> in the copied structure with <Color id="BLUE">Crafting Input Proxies</Color> linked back to the original bus! Again, the linking is automatic!

<FloatingImage src="./assets/mm_smart.png" wrap="square" align="left" width="256">
  <ImageAnnotation>
    The new Smart Copy menu
  </ImageAnnotation>
</FloatingImage>
<br clear="all"/>
# Decorative Block Support
The <Color id="GREEN">Matter Manipulator</Color> fully supports Carpenter's Blocks, Project Red, and Forge Microblocks, preserving their orientation and decorative covers.

## OpenComputers Cable Support
Cable Mode works with OpenComputers cables. Right click a cable to select, then start drawing lines, just like with Applied Energistics cables.
