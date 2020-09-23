---
title: Agregar encabezado de archivo
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44c3b64d9fb8944a578d054b7d98d4bf39bde3bc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810381"
---
# <a name="add-file-header"></a>Agregar encabezado de archivo

Esta generación de código se aplica a:

- C#

- Visual Basic

**Qué:** Adición de encabezados de archivo a archivos, proyectos y soluciones existentes con un archivo [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

**Cuándo:** quiere agregar fácilmente un encabezado de archivo a archivos, proyectos y soluciones.

**Por qué:** su equipo le pide que incluya un encabezado de archivo para indicar los derechos de autor. 

## <a name="how-to"></a>Procedimiento

1. Agregue un archivo [EditorConfig](../create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project) a un proyecto o a una solución si aún no tiene uno.

2. Agregue la regla siguiente al archivo EditorConfig: *file_header_template*.

3. Establezca el valor de la regla para que sea igual al texto de encabezado que quiere aplicar. Puede usar `{fileName}` como un marcador de posición para el nombre de archivo.

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