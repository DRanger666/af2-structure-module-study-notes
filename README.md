# AF2 Structure Module Study Notes

This repository contains personal **study notes** on the AlphaFold 2 (AF2) structure module, with a focus on the invariant point attention (IPA) mechanism and related geometric machinery.

The maintained sources are native LaTeX (`.tex`) files, and the primary way to read the notes is via the compiled PDF files.

## References

- Jumper, J. *et al.* (2021). Highly accurate protein structure prediction with AlphaFold. *Nature*, 596(7873), 583–589.  
  Article and open-access PDF: <https://www.nature.com/articles/s41586-021-03819-2>  

## LaTeX Files (sources) and PDFs (outputs)

LaTeX sources live in the `tex/` directory, and compiled PDFs live in the `pdf/` directory:

- `tex/af2_structure_module_full_walkthrough.tex` / `pdf/af2_structure_module_full_walkthrough.pdf`  
  Self-contained walkthrough of the AF2 structure module: frames, Algorithm 20, IPA (Algorithm 22), BackboneUpdate, FAPE, torsions, rigid groups, and overall loss.

- `tex/af2_ipa_point_features_detailed_explanation.tex` / `pdf/af2_ipa_point_features_detailed_explanation.pdf`  
  Detailed explanation of point features in IPA: scalar vs point Q/K/V, local vs global coordinates, frames, distance term in logits, point-valued outputs, and invariance.

- `tex/af2_ipa_point_features_alternative_explanation.tex` / `pdf/af2_ipa_point_features_alternative_explanation.pdf`  
  Alternative, more streamlined exposition of point features and how they fit into a “dot product + biases” view of attention.

- `tex/af2_ipa_viewed_as_standard_self_attention_at_its_core.tex` / `pdf/af2_ipa_viewed_as_standard_self_attention_at_its_core.pdf`  
  IPA interpreted as standard self-attention with additional bias terms (pair bias and geometric bias), emphasizing that Q/K/V + softmax remains the core.

- `tex/af2_ipa_invariance_and_equivariance_local_vs_global_coordinates_explanation.tex` / `pdf/af2_ipa_invariance_and_equivariance_local_vs_global_coordinates_explanation.pdf`  
  Focused on local vs global coordinates, rigid transforms, and why IPA’s logits and outputs are invariant to global SE(3) motions while BackboneUpdate is equivariant.

- `tex/af2_structure_module_algo20_transitionMLP_dropout_layernorm_deep_dive.tex` / `pdf/af2_structure_module_algo20_transitionMLP_dropout_layernorm_deep_dive.pdf`  
  Deep dive on Algorithm 20: Transition MLP + dropout + LayerNorm.

- `tex/rotations_and_invariance_background.tex` / `pdf/rotations_and_invariance_background.pdf`  
  General 3D geometry background: rotations, dot-product invariance, preserved quantities, and rigid motions in SE(3).

- `tex/af2_local_global_rigid_transforms_vs_change_of_basis.tex` / `pdf/af2_local_global_rigid_transforms_vs_change_of_basis.pdf`  
  Clarifies why AF2’s local–global frame maps are per-residue rigid transforms (elements of $\mathrm{SE}(3)$), not mere linear change-of-basis operations on a single vector space.

- `tex/af2_local_global_frames_visual_intuition.tex` / `pdf/af2_local_global_frames_visual_intuition.pdf`  
  Visual, coordinate-level intuition for why AF2 attaches local frames to residues and how this yields rotationally invariant geometric features.

## Building the PDFs

From the `tex/` directory, you can compile any note with `pdflatex` (or `xelatex`):

```bash
cd tex
pdflatex af2_structure_module_full_walkthrough.tex
pdflatex af2_ipa_point_features_detailed_explanation.tex
# etc.
```
