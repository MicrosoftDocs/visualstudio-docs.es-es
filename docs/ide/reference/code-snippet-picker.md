---
title: "Selector de fragmentos de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.expansionpicker"
helpviewer_keywords: 
  - "Selector de fragmentos de código"
  - "fragmentos de código, Selector de fragmentos de código"
  - "fragmentos de código de IntelliSense, Selector de fragmentos de código"
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 25
caps.handback.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Selector de fragmentos de c&#243;digo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El Editor de código de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dispone de un **Selector de fragmentos de código** que permite, con unos pocos clics del mouse, insertar bloques de código predefinidos en el documento activo.  
  
 El procedimiento para mostrar el **Selector de fragmentos de código** varía según el lenguaje que esté utilizando.  
  
-   [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: haga clic con el botón secundario en la ubicación que desee en el Editor de código para mostrar el menú contextual y seleccione **Insertar fragmento de código**.  
  
-   [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: haga clic con el botón secundario en la ubicación que desee en el Editor de código para mostrar el menú contextual y haga clic en **Insertar fragmento de código** o **Envolver con**.  
  
-   [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]: el **Selector de fragmentos de código** no está disponible.  
  
-   Visual F\# \- El **Selector de fragmentos de código** no está disponible.  
  
-   [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] \-\- Haga clic con el botón secundario en la ubicación que desee en el Editor de código para mostrar el menú contextual, y haga clic en **Insertar fragmento de código** o **Envolver con**.  
  
-   XML: haga clic con el botón secundario en la ubicación que desee en el Editor de código para mostrar el menú contextual, y haga clic en **Insertar fragmento de código** o **Envolver con**.  
  
-   HTML: haga clic con el botón secundario en la ubicación que desee en el Editor de código para mostrar el menú contextual, y haga clic en **Insertar fragmento de código** o **Envolver con**.  
  
-   SQL \- Haga clic con el botón secundario en la ubicación que desee en el Editor de código para mostrar el menú contextual y haga clic en **Insertar fragmento de código**.  
  
 En la mayoría de los lenguajes de desarrollo de Visual Studio, puede utilizar el  **Administrador de fragmentos de código** para agregar carpetas a la  **Lista de carpetas** que la  **Selector de fragmentos de código** busca archivos de fragmento XML.  También puede crear sus propios fragmentos de código para agregar a la lista.  Para obtener más información, vea [Tutorial: Crear un fragmento de código](../../ide/walkthrough-creating-a-code-snippet.md).  
  
## Lista de UIElement  
 Nombre del elemento  
 Un campo de texto modificable que muestra el nombre del elemento seleccionado en la **Lista de elementos**.  Para realizar una búsqueda incremental del elemento que desea, empiece a escribir su nombre en este campo.  Continúe agregando letras hasta que se seleccione el elemento que desea en la **Lista de elementos**.  
  
 Lista de elementos  
 Una lista de fragmentos de código que se pueden insertar, o una lista de carpetas que contienen fragmentos de código.  Para insertar un fragmento de código o expandir una carpeta, seleccione el elemento que desee y presione Entrar.  
  
## Vea también  
 [Procedimientos recomendados para usar fragmentos de código](../../ide/best-practices-for-using-code-snippets.md)   
 [Fragmentos de código de IntelliSense de Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
 [Establecer marcadores en el código](../../ide/setting-bookmarks-in-code.md)   
 [Cómo: Utilizar fragmentos de código envolventes](../../ide/how-to-use-surround-with-code-snippets.md)