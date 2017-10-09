# Model Lineage

A common usage of XDM is to create datasets and data objects that are derived from a core model, but also contain one or more application- or customer-specific properties.  It is desirable to be able to describe this situation easily and succinctly, while remaining conformance with standard JSON Schema processing.

To achieve this, XDM introduces a new keyword “derivedFrom”, which contains a reference to a parent model.  When present in the JSON Schema root, this signals that a model is derived from the parent and contains all of the properties defined by the parent.

When a model signals that it is a derived model, the model MUST be compatible with the parent model, where compatibility is defined as in XDM Compatibility.  Specifically, a derived model MUST NOT use the “not” keyword to invalidate any portion of the parent model.

When a reader observes that a model is a derived model, the reader MAY assume that the model is compatible with the parent model, where compatibility is defined as in Model Compatibility.

Details on the XDM syntax for model lineage can be found in ????.

# Model Compatibility

For an XDM model to be considered compatible with a second model, all data objects that validate under the first model MUST also validate under the second model.  The schema of the second model is the common schema between the two models.

A model MAY be compatible with multiple other models.  A common example of this is when two models are joined together to create a new schema to describe a joined/denormalized dataset.  XDML introduced a new keyword "implements" which provides a list of the XDM models that a given model is compatible with.  An example is shown in Appendix ????.

By definition of model lineage, a derived model MUST be compatible with its parent model.  See Model Lineage above for details.  A derived model MAY list its parent model in the implements section, but this is not required.

See ???? for details on the implements keyword.

