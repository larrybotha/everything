A [[security model]] that aims to achieve integrity using the following concepts:

- Constrained Data Item (CDI) : data whose integrity we want to preserve, e.g. rows in a database
- Unconstrained Data Item (UDI) : all data types beyond CDI, such as user and system input
- Transformation Procedures (TPs) : operations on data, such as reading and writing, and should maintain the integrity of CDIs
- Integrity Verification Procedures (IVPs) : procedures that check and ensure the validity of CDIs.



