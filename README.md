# Forward-Forward-Boosting
This repo contains boosting experiments with forward-forward algorithm that is supposed to combat deep layer underfitting observed while training..

# Problem
The deeper the layer in forward-forward algorithm, the more underfit it is given the same epoch count. The shallowest layer always fits the best and deeper layers don't contribute positively to any of the shallower layers goodness scores. This phenomenon is also described in layer collaboration in forward-forward algorithm paper.

# Key Technique
Using goodness scores for the next(deeper) layer as boosts for weakly classified inputs. The goodness scores are expected to weight the gradients towards previously poorly fitted inputs. While the parent cannot fit all data well, the sibling can by using it's new and unused capacity and constant scores of goodness of the parent.

# Pro's
*  Top-down: Train one layer at a time, training time memory efficient
*  Black-box: Goodness scores can come from any model/architecture/algorithm as long as it is correct or beneficial.
*  Layerwise validation: Layer depth growth can be moderated with validation.
*  Architecture searching: Multiple sources of goodness scores can be incorporated in direct acyclic graph pattern.

# Con's
*  Greediness: Algorithm is still greedy, cannot ensure generalization.
*  Lack of criterion diversity: All layers are oriented around the same criterion.

# Research Directions
The repo is supposed to adress (in future) these research directions summarized with the questions listed below. Many of them requires understanding of backpropagation and then interpretation of this understanding as criterion that can be interpolated with respect to depth.

*  Can wider layers be trained as fragments using a boosting technique? Can it be simulated?
*  Can any boosting mechanism outscore single wide layer in FF algorithm with the same memory and compute time constraints?
*  Can a layer produce a set of goodness scores such that when used in boosting the next layer is forced to learn higher level features?
*  How boosting in forward-forward differ in terms of features with boosting of backpropagated shallow networks?
