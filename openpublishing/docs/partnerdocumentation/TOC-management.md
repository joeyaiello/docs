# Building the TOC #

**TOC.md** is used to define the TOC (table of contents) structure of a docset. TOC is described in Markdown format.

We use Markdown headers to specify the level of the TOC. For example:
 ```markdown
# Tutorial
## Step 1
## Step 2
## Step 3
```

The above example illustrates a parent topic "Tutorial" with three children Step 1-3.

We use standard Markdown link syntax to specify the target topic of the toc node. For example:
  ```markdown
 # [Tutorial](tutorial.md)
 ## [Step 1](step-1.md)
 ## [Step 2](step-2.md)
 ## [Step 3](step-3.md)
```

If a toc node is not a link, it will become a container node (can contain children but cannot be clicked).

## Important information ##

-  The TOC for Open Publishing is a self-contained TOC not integrated into the global MSDN/TN TOC.
	-  You can use an external link to connect the Open Publishing TOC to your MSDN/TN Global TOC.
-  Since markdown only support 6 levels of header, we'll only support 6 levels of TOC for now. This can be extended in the future.
-  You cannot reference a file outside a docset/folder. For example, you cannot have a MD file at the same level than the TOC and reference to it from the TOC.
- TOC.md cannot contain arbitrary markdown content. For example, you cannot have images in it. All content that are not headers will lead to build error.

## Localized TOC ##
Localized TOC is maintained in sync with English via the handoff and handback process. TOC.md will be included in the handoff package. 
