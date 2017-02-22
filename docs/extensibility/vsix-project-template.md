---
title: "Plantilla de proyecto VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "implementar paquetes"
  - "publicar la extensión"
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Plantilla de proyecto VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede usar la plantilla de proyecto de VSIX para ajustar una o más extensiones de Visual Studio en un proyecto VSIX y, a continuación, publicar el paquete en el [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web.  
  
 Implementación de VSIX admite VSPackages, ensamblados, componentes MEF, plantillas de proyecto, plantillas de elementos, controles de cuadro de herramientas y tipos de extensión personalizados.  
  
> [!NOTE]
>  Para usar proyectos VSIX, debe instalar el SDK de Visual Studio. Para obtener más información sobre el SDK de Visual Studio, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## Dónde encontrar la plantilla de proyecto VSIX  
 La plantilla de proyecto VSIX está disponible en la **nuevo proyecto** cuadro de diálogo. Expanda el **Visual Basic** nodo o **Visual C\#** nodo y, a continuación, elija **extensibilidad**.  
  
> [!TIP]
>  Debe asegurarse de que .NET Framework 4.5 o posterior, se especifica en la lista desplegable en la parte superior de la **nuevo proyecto** cuadro de diálogo.  
  
## Usos de la plantilla de proyecto VSIX  
 La plantilla de proyecto VSIX tiene dos usos principales:  
  
-   Para implementar plantillas de proyecto, plantillas de elementos y otras extensiones que no dispone de soporte técnico VSIX.  
  
-   Para ajustar los resultados de varias extensiones en un paquete de distribución.  
  
 No es necesario utilizar la plantilla de proyecto de VSIX para implementar VSPackages u otros tipos de extensiones que disponen de VSIX.  
  
## Empaquetar una extensión en un proyecto VSIX vacío  
 Puede empaquetar una extensión existente o una extensión que no tiene todavía VSIX admiten ajustando en un proyecto VSIX vacío. La extensión se ajuste debe ser de un tipo que es compatible con la [esquema VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
#### Para empaquetar una extensión utilizando un proyecto VSIX  
  
1.  Compile los proyectos que forman la extensión.  
  
2.  Cree un proyecto VSIX utilizando la **proyecto VSIX** plantilla.  
  
     Se abre Source.Extension.vsixmanifest en **Diseñador de manifiestos**.  
  
3.  En la pestaña **Activos**, elija el botón **Nuevo**.  
  
     Aparecerá el cuadro de diálogo **Agregar nuevo activo**.  
  
4.  En el **tipo** elija el tipo de extensión que se va a agregar.  
  
5.  Para agregar un elemento de extensión o contenido que se incluye en la solución actual \(por ejemplo, una plantilla de elemento o un ensamblado compilado\), realice los pasos siguientes:  
  
    1.  En la lista **Origen**, elija **Un proyecto de la solución actual**.  
  
    2.  En el **proyecto** elija el nombre de la extensión.  
  
    3.  En el **incrustar en esta carpeta** escriba el nombre de una carpeta en la que desea incrustar el recurso y, a continuación, elija la **Aceptar** botón.  
  
6.  Para agregar una extensión o un elemento de contenido que no está incluido en la solución actual, realice los pasos siguientes:  
  
    1.  En el **origen** cuadro de lista, elija **archivo en filesystem**.  
  
    2.  En el **ruta** campo, escriba la ruta de acceso completa al archivo de extensión compilado o comprimido o utilizar el **Examinar** botón para examinar el archivo.  
  
    3.  En el **incrustar en esta carpeta** escriba el nombre de una carpeta en la que desea incrustar el recurso y, a continuación, elija la **Aceptar** botón.  
  
7.  Si desea que el paquete debe incluir extensiones adicionales, agregar de la misma manera.  
  
8.  Compile la solución.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera un archivo .vsix que contiene un archivo de manifiesto de VSIX, un archivo \[Content\_Types\] .xml y todos los activos de extensión que agrega al proyecto.  
  
## Vea también  
 [Referencia de esquema 2.0 extensión VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)