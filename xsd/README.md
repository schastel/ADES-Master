For what it's worth... No guarantee of correctness, of completion,
actually... No guarantee at all.

The submit-xml-sc.xml is not endorsed by the MPC, the IAU, or anyone
at Pan-STARRS. If you decide to use it, it's at your own risks.

I tried to extend the original submit.xsd by implementing the checks
performed at the MPC given by M. Rudenko (see
https://github.com/IAU-ADES/ADES-Master/issues/5) and the constraints
described at
https://www.minorplanetcenter.net/iau/info/ADESFieldValues.html

I use the submit-mpc-sc.xsd with xmllint (available in any Linux
distribution) this way:
xmllint --schema submit-mpc.xsd --noout my_submissions.xml

I ran it on twenty-ish Pan-STARRS submission batches without issues.

Error messages examples if you're not used to xmllint output:

* 0126240.xml:52: element rmsMag: Schemas validity error : Element 'rmsMag': [facet 'maxInclusive'] The value '28026532265984.00' is greater than the maximum value allowed ('999999.0').
0126240.xml:52: element rmsMag: Schemas validity error : Element 'rmsMag': '28026532265984.00' is not a valid value of the atomic type 'RmsMagType'.

... means that in file 0126240.xml at line 52, the element rmsMag containing the value 28026532265984.00 is greater than the maximum value allowed

* astCat-wrong.xml:50: element astCat: Schemas validity error : Element 'astCat': 'GAIA1' is not a valid value of the union type 'AstCatType'.

It should be Gaia1 not GAIA1

