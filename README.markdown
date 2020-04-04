# PdfiumViewer.Code

将pvginkel/PdfiumViewer做了.Net Core 3.1的移植

## NuGet

```
Install-Package PdfiumViewer.Core
```

```
Install-Package PdfiumViewer.Native.x86_64.v8-xfa
Install-Package PdfiumViewer.Native.x86.v8-xfa
```

## 介绍

PdfiumViewer是基于PDFium项目的PDF查看器。

PdfiumViewer提供了许多用于处理PDF文件的组件：

PdfDocument是用于呈现PDF文档的基类；

PdfRenderer是一个WinForms控件，可以呈现PdfDocument；

PdfiumViewer是一个WinForms控件，它承载一个PdfRenderer控件，并且添加了一个工具栏来保存或打印PDF文件。

## Compatibility

The PdfiumViewer library has been tested with Windows XP , Windows 8 and Windows 10, and
is fully compatible with both. However, the native PDFium libraries with V8
support do not support Windows XP. See below for instructions on how to
reference the native libraries.

## Using the library

The PdfiumViewer control requires native PDFium libraries. These are not included
in the PdfiumViewer NuGet package. See the [Installation instructions](https://github.com/pvginkel/PdfiumViewer/wiki/Installation-instructions)
Wiki page for more information on how to add these.

## Note on the `PdfViewer` control

The PdfiumViewer library primarily consists out of three components:

* The `PdfViewer` control. This control provides a host for the `PdfRenderer`
  control and has a default toolbar with limited functionality;
* The `PdfRenderer` control. This control implements the raw PDF renderer.
  This control displays a PDF document, provides zooming and scrolling
  functionality and exposes methods to perform more advanced actions;
* The `PdfDocument` class provides access to the PDF document and wraps
  the Pdfium library.

The `PdfViewer` control should only be used when you have a very simple use
case and where the buttons available on the toolbar provide enough functionality
for you. This toolbar will not be extended with new buttons or with functionality
to hide buttons. The reason for this is that the `PdfViewer` control is just
meant to get you started. If you need more advanced functionality, you should
create your own control with your own toolbar, e.g. by starting out with
the `PdfViewer` control. Also, because people currently are already using the
`PdfViewer` control, adding more functionality to this toolbar would be
a breaking change. See [issue #41](https://github.com/pvginkel/PdfiumViewer/issues/41)
for more information.

## Building PDFium

Instructions to build the PDFium library can be found on the [Building PDFium](https://github.com/pvginkel/PdfiumViewer/wiki/Building-PDFium)
wiki page. However, if you are just looking to use the PdfiumViewer component
or looking for a compiled version of PDFium, these steps are not required.
NuGet packages with precompiled PDFium libraries are made available for
usage with PdfiumViewer. See the chapter on **Using the library** for more
information.

Alternatively, the [PdfiumBuild](https://github.com/pvginkel/PdfiumBuild) project
is provided to automate building PDFium. This project contains scripts to
build PdfiumViewer specific versions of the PDFium library. This project
is configured on a build server to compile PDFium daily. Please refer to
the [PdfiumBuild](https://github.com/pvginkel/PdfiumBuild) project page
for the location of the output of the build server. The PdfiumViewer specific
libraries are located in the `PdfiumViewer-...` target directories.

## License

PdfiumViewer is licensed under the Apache 2.0 license. See the license details for how PDFium is licensed.
