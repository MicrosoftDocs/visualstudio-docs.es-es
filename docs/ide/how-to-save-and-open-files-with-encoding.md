---
title: 'Cómo: Guardar y abrir archivos con codificación'
description: Aprenda a guardar y abrir archivos con una codificación específica, de forma que, cuando abra un archivo, Visual Studio lo muestre correctamente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d19b6f8e2e614ed397dee2e75807ded895a82d81
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927917"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Cómo: Guardar y abrir archivos con codificación

Puede guardar archivos con codificación de caracteres específicos para admitir lenguajes bidireccionales. Además puede especificar una codificación al abrir un archivo para que Visual Studio lo muestre correctamente.

## <a name="to-save-a-file-with-encoding"></a>Para guardar un archivo con codificación

1. En el menú **Archivo**, elija **Guardar archivo como** y luego haga clic en el botón desplegable situado junto al botón **Guardar**.

     Se muestra el cuadro de diálogo **Opciones avanzadas para guardar**.

2. En **Codificación**, seleccione la codificación que quiere usar para el archivo.

3. Opcionalmente, en **Fin de línea**, seleccione el formato de los caracteres de fin de línea.

     Esta opción es útil si va a intercambiar el archivo con usuarios de otro sistema operativo.

     Si quiere trabajar con un archivo que sabe que está codificado de una forma concreta, puede indicar a Visual Studio que use esa codificación al abrirlo. El método que use depende de si el archivo forma parte del proyecto.

> [!NOTE]
> Si quiere guardar el archivo del proyecto con codificación, la opción **Guardar archivo como** no está habilitada hasta que no descarga el proyecto.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Para abrir un archivo codificado que forma parte de un proyecto

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el archivo y elija **Abrir con**.

2. En el cuadro de diálogo **Abrir con**, elija el editor con el que abrir el archivo.

     La mayoría de los editores de Visual Studio, como el editor de formularios, detecta automáticamente la codificación y abre el archivo correctamente. Si elige un editor que permite seleccionar una codificación, se muestra el cuadro de diálogo **Codificación**.

3. En el cuadro de diálogo **Codificación**, seleccione la codificación que debe usar el editor.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Para abrir un archivo codificado que no forma parte de un proyecto

1. En el menú **Archivo**, seleccione **Abrir**, **Archivo** o **Archivo de Web** y luego seleccione el archivo que quiere abrir.

2. Haga clic en el botón desplegable situado junto al botón **Abrir** y elija **Abrir con**.

3. Siga los pasos 2 y 3 del procedimiento anterior.

## <a name="see-also"></a>Consulte también

- [Codificación y saltos de línea](encodings-and-line-breaks.md)
- [Codificación y globalización de Windows Forms](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalizar y localizar aplicaciones](../ide/globalizing-and-localizing-applications.md)
