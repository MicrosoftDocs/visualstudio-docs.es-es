---
title: Selector de fragmentos de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2918826d6923efa3db42f4f572c416b9668513a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660896"
---
# <a name="code-snippet-picker"></a>Selector de fragmentos de código
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El Editor de código de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] proporciona un **selector de fragmentos de código** que permite, con unos pocos clics de mouse, insertar bloques de código predefinidos en el documento activo.

 El procedimiento para mostrar el **selector de fragmentos de código** varía según el idioma que esté usando.

- [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código**.

- [!INCLUDE[csprcs](../../includes/csprcs-md.md)] -Haga clic con el botón derecho en la ubicación deseada en el editor de código para mostrar el menú contextual y haga clic en **Insertar fragmento** de código o **envolver con**.

- [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] - El **selector de fragmentos de código** no está disponible.

- Visual F# - El **selector de fragmentos de código** no está disponible.

- [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] -- Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.

- XML - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.

- HTML - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.

- SQL - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código**.

  En la mayoría de los lenguajes de desarrollo de Visual Studio, puede usar el **Administrador de fragmentos de código** para agregar carpetas a la lista de **carpetas** donde el selector de fragmentos de código busca archivos de fragmento de **código** XML. También puede crear sus propios fragmentos de código para agregarlos a la lista. Para obtener más información, vea [Tutorial: crear un fragmento de código](../../ide/walkthrough-creating-a-code-snippet.md).

## <a name="uielement-list"></a>Lista de UIElement
 Nombre de elemento campo de texto modificable que muestra el nombre del elemento seleccionado en la **lista de elementos**. Para realizar una búsqueda incremental para el elemento que quiera, empiece escribiendo su nombre en este campo. Continúe agregando letras hasta que el elemento que busca se haya seleccionado en la **lista de elementos**.

 Elemento muestra una lista de fragmentos de código disponibles para la inserción, o una lista de carpetas que contienen fragmentos de código. Para insertar un fragmento de código o expandir una carpeta, seleccione el elemento que quiera y presione Entrar.

## <a name="see-also"></a>Consulte también
 [Prácticas recomendadas para usar fragmentos de código](../../ide/best-practices-for-using-code-snippets.md) [Visual Basic fragmentos de código de IntelliSense](https://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643) [establecer marcadores en el código](../../ide/setting-bookmarks-in-code.md) [Cómo: usar fragmentos de código envolventes](../../ide/how-to-use-surround-with-code-snippets.md)
