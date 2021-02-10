---
title: Selector de fragmentos de código
description: Aprenda a usar el Selector de fragmentos de código para insertar bloques de código predefinidos en el documento activo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 93fea67056c73a6e9b0b265253479fbecee63767
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956157"
---
# <a name="code-snippet-picker"></a>Selector de fragmentos de código

El Editor de código de Visual Studio proporciona un **selector de fragmentos de código** que permite, con unos pocos clics de mouse, insertar bloques de código predefinidos en el documento activo.

El procedimiento para mostrar el **selector de fragmentos de código** varía según el idioma que esté usando.

- Visual Basic: Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código**.

- C#: Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.

- C++: El **selector de fragmentos de código** no está disponible.

- F#: El **selector de fragmentos de código** no está disponible.

- JavaScript: Haga clic con el botón derecho en la ubicación que quiera en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.

- XML - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.

- HTML - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código** o **Delimitar con**.

- SQL - Haga clic con el botón derecho en la ubicación deseada en el Editor de código para mostrar el menú contextual y elija **Insertar fragmento de código**.

En la mayoría de los lenguajes de desarrollo de Visual Studio, puede usar el **Administrador de fragmentos de código** para agregar carpetas a la lista de carpetas donde el **selector de fragmentos de código** busca archivos de fragmento de código XML. También puede crear sus propios fragmentos de código para agregarlos a la lista. Para más información, vea [Tutorial: Crear un fragmento de código](../../ide/walkthrough-creating-a-code-snippet.md).

## <a name="uielement-list"></a>Lista de UIElement

Nombre del elemento

Un campo de texto editable que muestra el nombre del elemento seleccionado en la **lista de elementos**. Para realizar una búsqueda incremental para el elemento que quiera, empiece escribiendo su nombre en este campo. Continúe agregando letras hasta que el elemento que busca se haya seleccionado en la **lista de elementos**.

Lista de elementos

Una lista de fragmentos de código disponibles para insertarlos o una lista de carpetas que contienen fragmentos de código. Para insertar un fragmento de código o expandir una carpeta, seleccione el elemento que quiera y presione Entrar.

## <a name="see-also"></a>Consulte también

- [Procedimientos recomendados para usar fragmentos de código](../../ide/best-practices-for-using-code-snippets.md)
- [Fragmentos de código de IntelliSense de Visual Basic](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Establecer marcadores en el código](../../ide/setting-bookmarks-in-code.md)
- [Cómo: Usar fragmentos de código envolventes](../../ide/how-to-use-surround-with-code-snippets.md)
