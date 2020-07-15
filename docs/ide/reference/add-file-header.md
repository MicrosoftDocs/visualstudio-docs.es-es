---
title: Agregar encabezado de archivo
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 779092e277ac5b6eed3afcaceaf55b26ee2759dd
ms.sourcegitcommit: 025816f8e388b29e58761d304b0fda755ac5a613
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374174"
---
# <a name="add-file-header"></a>Agregar encabezado de archivo

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Adición de encabezados de archivo a archivos, proyectos y soluciones existentes con un archivo [EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project).

**Cuándo:** quiere agregar fácilmente un encabezado de archivo a archivos, proyectos y soluciones.

**Por qué:** su equipo le pide que incluya un encabezado de archivo para indicar los derechos de autor. 

## <a name="how-to"></a>Procedimiento

1. Agregue un archivo [EditorConfig](https://docs.microsoft.com/visualstudio/ide/create-portable-custom-editor-options#add-an-editorconfig-file-to-a-project) a un proyecto o a una solución si aún no tiene uno.

2. Agregue la regla siguiente al archivo EditorConfig: *file_header_template*.

3. Establezca el valor de la regla para que sea igual al texto de encabezado que quiere aplicar.

    ![Regla de encabezado de archivo de EditorConfig](media/add-file-header-rule.png)

> [!NOTE]
> No puede tener multilíneas explícitas en un archivo EditorConfig, y deberá usar el carácter de nueva línea de Unix para insertar nuevas líneas.

4. Coloque el símbolo de intercalación en la primera línea de cualquier archivo de C# o de Visual Basic.

5. Presione **Ctrl**+ **.** para activar el menú **Acciones rápidas y refactorizaciones**.

6. Seleccione **Agregar encabezado de archivo**. 

    ![Regla de encabezado de archivo de EditorConfig](media/add-file-header.png)

7. Para aplicar el encabezado de archivo a un proyecto o a una solución completos, seleccione **Proyecto** o **Solución** en la opción **Corregir todas las repeticiones de:** .

8. Se abre el cuadro de diálogo **Corregir todas las repeticiones** donde puede obtener una vista previa de los cambios.

    ![Cuadro de diálogo Corregir todas las repeticiones](media/file-header-preview-changes.png)

8. Seleccione **Aplicar** para aplicar los cambios.

## <a name="see-also"></a>Vea también

- [Generación de código](../code-generation-in-visual-studio.md)
- [Vista previa de cambios](../../ide/preview-changes.md)
