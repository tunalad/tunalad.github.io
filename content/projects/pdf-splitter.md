+++
title = 'PDF-splitter'
date = 2023-11-09T22:33:05+01:00
description = "Extract specific pages from PDF documents."
tags = ["gui"]
tech = ["python", "qt"]
weight = 30
notable = false
github = "https://github.com/tunalad/pdf-splitter"
+++

PDF-splitter is a user-friendly GUI tool designed to extract pages from a PDF document. GUI part was done via Qt, so (in theory) it should work on all systems

Originally developed as a project for the SCS (Specialized Computer Systems) course, it continues to receive occasional updates.

![dashboard with a document](/images/pdf-splitter/img1.png)

## 1. Usage

The process is straightforward: locate a document and load it.
Upon loading, each page of the document is converted into an image (as depicted above).

Now you have two options for exporting the pages: either by selection or range.

### 1.1 By selection

Splitting by selection allows you to extract pages by manually clicking on the desired pages within the document. After selecting you pages, you'll have to check "Split by selection" option on the side. Hitting the "Extract pages" options, you'll get a single document of chosen pages. If you prefer each page exported individually, make sure to leave the "Merge all into one file" option unchecked. This way, each selected page will be saved as a separate document, providing a tailored and efficient extraction process.

### 1.2 By range

When you check the "Split by range" option, you gain the ability to specify a range of pages for exporting the document. For example, if your document consists of 15 pages, input 5 into the "Range from" field and 9 into the "Range to" field. When you export the document, it will generate a new document comprising pages 5 to 9 from the original document.
