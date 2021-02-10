---
title: 'Cómo: volver a habilitar un complemento de VSTO que se ha deshabilitado'
description: Obtenga información sobre cómo puede usar Visual Studio para volver a habilitar un complemento de VSTO que se ha deshabilitado en una aplicación Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VST.Warning.DisabledAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disabled add-ins
- add-ins [Office development in Visual Studio], disabled
- add-ins [Office development in Visual Studio], enabling
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: de3e251c15699ce29b7986e4f0cc19a3f5c5798d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942195"
---
# <a name="how-to-re-enable-a-vsto-add-in-that-has-been-disabled"></a>Cómo: volver a habilitar un complemento de VSTO que se ha deshabilitado
  Las aplicaciones de Microsoft Office pueden deshabilitar los complementos de VSTO que se comporten de forma inesperada. Si una aplicación no carga el complemento de VSTO cuando intenta depurarlo, la aplicación podría haber deshabilitado total o parcialmente el complemento de VSTO.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="hard-disabled-vsto-add-ins"></a>Complementos de VSTO deshabilitados de forma rígida
 La deshabilitación fuerte puede producirse cuando un complemento de VSTO hace que la aplicación se cierre de forma inesperada. También puede ocurrir en el equipo de desarrollo si detiene el depurador mientras se está ejecutando el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> en el complemento de VSTO.

### <a name="to-re-enable-a-vsto-add-in"></a>Para volver a habilitar un complemento de VSTO

1. En la aplicación, haga clic en la pestaña **Archivo** .

2. Haga clic en el botón **Opciones** de *applicationName* .

3. En el panel de categorías, haga clic en **Complementos**.

4. En el panel de detalles, compruebe que el complemento de VSTO aparece en la lista **Complementos de aplicación deshabilitados** .

     La columna **Nombre** especifica el nombre del ensamblado y la columna **Ubicación** especifica la ruta de acceso completa del manifiesto de aplicación.

5. En el cuadro **Administrar** , haga clic en **Elementos deshabilitados** y, a continuación, haga clic en **Ir**.

6. Seleccione el complemento de VSTO y haga clic en **Habilitar**.

7. Haga clic en **Cerrar**.

## <a name="soft-disabled-vsto-add-ins"></a>Complementos de VSTO deshabilitados temporalmente
 La deshabilitación parcial puede producirse cuando un complemento de VSTO genera un error que no hace que la aplicación se cierre inesperadamente. Por ejemplo, una aplicación podría deshabilitar parcialmente un complemento de VSTO si produce una excepción no controlada mientras se ejecuta el controlador de eventos <xref:Microsoft.Office.Tools.AddIn.Startup> .

> [!NOTE]
> Al volver a habilitar un complemento de VSTO deshabilitado parcialmente, la aplicación intenta cargar el complemento de VSTO de inmediato. Si no se corrige el problema que hizo inicialmente que la aplicación deshabilitara parcialmente el complemento de VSTO, la aplicación volverá a deshabilitar parcialmente el complemento de VSTO.

### <a name="to-re-enable-a-vsto-add-in"></a>Para volver a habilitar un complemento de VSTO

1. En la aplicación, haga clic en la pestaña **Archivo** .

2. Haga clic en el botón **Opciones** de *applicationName* .

3. En el panel de categorías, haga clic en **Complementos**.

4. En el panel de detalles, compruebe que el complemento de VSTO aparece en la lista **Complementos de aplicación inactivos** .

     La columna **Nombre** especifica el nombre del ensamblado y la columna **Ubicación** especifica la ruta de acceso completa del manifiesto de aplicación.

5. En el cuadro **Administrar** , haga clic en **Complementos COM** y, a continuación, haga clic en **Ir**.

6. En el cuadro de diálogo **Complementos COM** , seleccione la casilla situada al lado del complemento de VSTO deshabilitado.

7. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
- [Compilar soluciones de Office](../vsto/building-office-solutions.md)
- [Depurar proyectos de Office](../vsto/debugging-office-projects.md)
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
