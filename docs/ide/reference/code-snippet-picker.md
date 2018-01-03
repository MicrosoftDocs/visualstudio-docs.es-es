---
title: "Selector de fragmentos de código | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e352baf834f026462cb35921f7f79e75b3aecd96
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="code-snippet-picker"></a>Selector de fragmentos de código
El Editor de código de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona un **selector de fragmentos de código** que permite, con unos pocos clics de mouse, insertar bloques de código predefinidos en el documento activo.  
  
 El procedimiento para mostrar el **selector de fragmentos de código** varía según el idioma que esté usando.  
  
-   [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código**.  
  
-   [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.  
  
-   [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] - El **selector de fragmentos de código** no está disponible.  
  
-   Visual F# - El **selector de fragmentos de código** no está disponible.  
  
-   [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] -- Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.  
  
-   XML - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.  
  
-   HTML - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.  
  
-   SQL - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código**.  
  
En la mayoría de los lenguajes de desarrollo de Visual Studio, puede usar el **Administrador de fragmentos de código** para agregar carpetas a la **lista de carpetas** donde el **selector de fragmentos de código** busca archivos de fragmento de código XML. También puede crear sus propios fragmentos de código para agregarlos a la lista. Para obtener más información, vea [Tutorial: Crear un fragmento de código](../../ide/walkthrough-creating-a-code-snippet.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
Nombre del elemento  
Un campo de texto editable que muestra el nombre del elemento seleccionado en la **lista de elementos**. Para realizar una búsqueda incremental para el elemento que quiera, empiece escribiendo su nombre en este campo. Continúe agregando letras hasta que el elemento que busca se haya seleccionado en la **lista de elementos**.  
  
Lista de elementos  
Una lista de fragmentos de código disponibles para insertarlos o una lista de carpetas que contienen fragmentos de código. Para insertar un fragmento de código o expandir una carpeta, seleccione el elemento que quiera y presione Entrar.  
  
## <a name="see-also"></a>Vea también  
[Procedimientos recomendados para usar fragmentos de código](../../ide/best-practices-for-using-code-snippets.md)   
[Fragmentos de código de IntelliSense de Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)   
[Establecer marcadores en el código](../../ide/setting-bookmarks-in-code.md)   
[Cómo: Usar fragmentos de código envolventes](../../ide/how-to-use-surround-with-code-snippets.md)