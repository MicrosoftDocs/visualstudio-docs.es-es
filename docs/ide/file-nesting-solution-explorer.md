---
title: Reglas de anidamiento de archivos para el Explorador de soluciones
description: Aprenda sobre las reglas de anidamiento de archivos, los valores preestablecidos y la personalización del Explorador de soluciones.
ms.custom: SEO-VS-2020
ms.date: 05/25/2018
ms.topic: conceptual
helpviewer_keywords:
- file nesting
- Solution Explorer, file nesting
author: angelosp
ms.author: angelpe
manager: jmartens
ms.openlocfilehash: aa3ca640fed4e32c19defd925a49369890219035
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869458"
---
# <a name="file-nesting-in-solution-explorer"></a>Anidamiento de archivos en el Explorador de soluciones

El **Explorador de soluciones** anida archivos relacionados para ayudarle a organizarlos y que sean más fáciles de localizar. Por ejemplo, si agrega un formulario Windows Forms a un proyecto, el archivo de código para el formulario está anidado debajo del formulario en el **Explorador de soluciones**. En los proyectos de ASP.NET Core, el anidamiento de archivos se puede llevar un paso más lejos. Puede elegir entre los valores preestablecidos de anidamiento de archivos **Desactivado**, **Predeterminado** y **Web**. También puede [personalizar cómo se anidan los archivos](#customize-file-nesting) o [crear una configuración específica de la solución y del proyecto](#create-project-specific-settings).

> [!NOTE]
> Actualmente, la característica solo se admite para los proyectos de ASP.NET Core.

## <a name="file-nesting-options"></a>Opciones de anidamiento de archivos

![Botón para activar y desactivar el anidamiento de archivos](media/filenesting_onoff.png)

Las opciones disponibles para el anidamiento de archivos no personalizado son:

* **Desactivado**: esta opción le ofrece una lista plana de archivos sin anidamiento.

* **Predeterminado**: esta opción proporciona el comportamiento de anidamiento de archivos predeterminado en el **Explorador de soluciones**. Si no existe ninguna configuración para un tipo de proyecto determinado, los archivos del proyecto no se anidan. Si existen una configuración, por ejemplo, para un proyecto web, se aplica el anidamiento.

* **Web**: esta opción aplica el comportamiento de anidamiento **Web** a todos los proyectos de la solución actual. Le animamos a que eche un vistazo a sus numerosas reglas y nos dé su opinión. En la captura de pantalla siguiente se resaltan algunos ejemplos del comportamiento de anidamiento de archivos que se obtiene con esta opción:

   ![Anidamiento de archivos en el Explorador de soluciones](media/filenesting.png)

## <a name="customize-file-nesting"></a>Personalizar el anidamiento de archivos

Si no le gustan las opciones incluidas de fábrica, puede crear su propia configuración de anidamiento de archivos para indicarle al **Explorador de soluciones** cómo se deben anidar los archivos. Puede agregar tantas configuraciones personalizadas de anidamiento de archivos como desee, y puede cambiar entre ellas según sea necesario. Para crear una nueva configuración personalizada, puede empezar con un archivo vacío o puede usar la configuración **Web** como punto de partida:

![Agregar reglas de anidamiento de archivos personalizadas](media/filenesting_addcustom.png)

Le recomendamos que use la configuración **Web** como punto de partida, ya que es más fácil trabajar con algo que ya funciona. Si usa la configuración **Web** como punto de partida, el archivo *.filenesting.json* tiene un aspecto similar al siguiente:

![Usar reglas existentes de anidamiento de archivos como base para la configuración personalizada](media/filenesting_editcustom.png)

Centrémonos en el nodo **dependentFileProviders** y en sus nodos secundarios. Cada nodo secundario es un tipo de regla que Visual Studio puede usar para anidar archivos. Por ejemplo, **tener el mismo nombre de archivo, pero otra extensión** es un tipo de regla. Las reglas disponibles son:

* **extensionToExtension**: use este tipo de regla para anidar *file.js* en *file.ts*.

* **fileSuffixToExtension**: use este tipo de regla para anidar *file-vsdoc.js* en *file.js*.

* **addedExtension**: use este tipo de regla para anidar *file.html.css* en *file.html*.

* **pathSegment**: use este tipo de regla para anidar *jquery.min.js* en *jquery.js*.

* **allExtensions**: use este tipo de regla para anidar *file.** en *file.js*.

* **fileToFile**: use este tipo de regla para anidar *bower.json* en *.bowerrc*.

### <a name="the-extensiontoextension-provider"></a>Proveedor extensionToExtension

Este proveedor permite definir reglas de anidamiento de archivos mediante determinadas extensiones de archivo. Considere el ejemplo siguiente:

![Ejemplo de reglas extentionToExtension](media/filenesting_extensiontoextension.png) ![Efecto del ejemplo extentionToExtension](media/filenesting_extensiontoextension_effect.png)

* *Cart.js* está anidado en *cart.ts* debido a la primera regla **extensionToExtension**.

* *cart.js* no está anidado en *cart.tsx* porque **.ts** está antes que **.tsx** en las reglas, y solo puede haber un elemento primario.

* *light.css* está anidado en *light.sass* debido a la segunda regla **extensionToExtension**.

* *home.html* está anidado en *home.md* debido a la tercera regla **extensionToExtension**.

### <a name="the-filesuffixtoextension-provider"></a>Proveedor fileSuffixToExtension

Este proveedor funciona igual que el proveedor **extensionToExtension**, con la única diferencia que la regla tiene en cuenta el sufijo del archivo en lugar de simplemente la extensión. Considere el ejemplo siguiente:

![Ejemplo de reglas fileSuffixToExtension](media/filenesting_filesuffixtoextension.png) ![Efecto del ejemplo fileSuffixToExtension](media/filenesting_filesuffixtoextension_effect.png)

* *portal-vsdoc.js* está anidado en *portal.js* debido a la regla **fileSuffixToExtension**.

* Todos los demás aspectos de la regla funcionan del mismo modo que **extensionToExtension**.

### <a name="the-addedextension-provider"></a>Proveedor addedExtension

Este proveedor anida archivos con una extensión adicional bajo el archivo sin extensión adicional. La extensión adicional solo puede aparecer al final del nombre de archivo completo.

Considere el ejemplo siguiente:

![Ejemplo de reglas addedExtension](media/filenesting_addedextension.png) ![Efecto del ejemplo addedExtension](media/filenesting_addedextension_effect.png)

* *file.html.css* está anidado en *file.html* debido a la regla **addedExtension**.

> [!NOTE]
> No especifica ninguna extensión de archivo para la regla `addedExtension`, así que se aplica automáticamente a todas las extensiones de archivo. Es decir, cualquier archivo con el mismo nombre y extensión que otro archivo más una extensión adicional al final se anida debajo del otro archivo. No puede limitar el efecto de este proveedor a solo extensiones de archivo específicas.

### <a name="the-pathsegment-provider"></a>Proveedor pathSegment

Este proveedor anida archivos con una extensión adicional bajo un archivo sin extensión adicional. La extensión adicional solo puede aparecer en mitad del nombre de archivo completo.

Considere el ejemplo siguiente:

![Ejemplo de reglas pathSegment](media/filenesting_pathsegment.png) ![Efecto del ejemplo pathSegment](media/filenesting_pathsegment_effect.png)

* *jquery.min.js* esta anidado en *jquery.js* debido a la regla **pathSegment**.

> [!NOTE]
> - Si no especifica extensiones de archivo concretas para la regla `pathSegment`, se aplica a todas las extensiones de archivo. Es decir, cualquier archivo con el mismo nombre y extensión que otro archivo más una extensión adicional en el medio se anida debajo del otro archivo.
> - Puede limitar el efecto de la regla `pathSegment` a extensiones de archivo específicas de la siguiente manera:
>
>    ```json
>    "pathSegment": {
>       "add": {
>         ".*": [
>           ".js",
>           ".css",
>           ".html",
>           ".htm"
>         ]
>       }
>    }
>    ```

### <a name="the-allextensions-provider"></a>Proveedor allExtensions

Este proveedor permite definir las reglas de anidamiento de archivos para archivos con cualquier extensión, pero el mismo nombre de archivo base. Considere el ejemplo siguiente:

![Reglas del ejemplo allExtensions](media/filenesting_allextensions.png) ![Efecto del ejemplo allExtensions](media/filenesting_allextensions_effect.png)

* *template.cs* y *template.doc* están anidados en *template.tt* debido a la regla **allExtensions**.

### <a name="the-filetofile-provider"></a>Proveedor fileToFile

Este proveedor permite definir las reglas de anidamiento de archivos basándose en los nombres de archivo completos. Considere el ejemplo siguiente:

![Ejemplos de reglas fileToFile](media/filenesting_filetofile.png) ![Efecto del ejemplo fileToFile](media/filenesting_filetofile_effect.png)

* *.bowerrc* está anidado en *bower.json* debido a la regla **fileToFile**.

### <a name="rule-order"></a>Orden de las reglas

El orden es importante en todas las partes del archivo de configuración personalizada. Puede cambiar el orden en que se ejecutan las reglas moviéndolas arriba o abajo dentro del nodo **dependentFileProvider**. Por ejemplo, si tiene una regla que hace que **file.js** sea el elemento primario de **file.ts**, y otra regla que hace que **file.coffee** sea el elemento primario de **file.ts**, el orden en que aparecen en el archivo dicta el comportamiento de anidamiento cuando los tres archivos están presentes. Puesto que **file.ts** solo puede tener un elemento primario, la regla que se ejecuta primero es la que tiene prioridad.

El orden también es importante para las secciones de la regla, no solo para los archivos de una sección. En el momento en que un par de archivos coinciden con una regla de anidamiento de archivos, las demás reglas inferiores del archivo se omiten y se procesa el siguiente par de archivos.

### <a name="file-nesting-button"></a>Botón de anidamiento de archivos

Toda la configuración, incluida la personalizada, se puede administrar mediante el mismo botón del **Explorador de soluciones**:

![Activar reglas de anidamiento de archivos personalizadas](media/filenesting_activatecustom.png)

## <a name="create-project-specific-settings"></a>Creación de una configuración específica del proyecto

Puede crear una configuración específica de la solución y del proyecto desde el menú contextual de la solución y el proyecto:

![Reglas de anidamiento específicas de la solución y el proyecto](media/filenesting_solutionprojectspecific.png)

La configuración específica de la solución y el proyecto se combina con la configuración activa de Visual Studio. Por ejemplo, puede tener un archivo de configuración específica del proyecto en blanco, y que los archivos se sigan anidando en el **Explorador de soluciones**. El comportamiento de anidamiento procede de la configuración específica de la solución o de la configuración de Visual Studio. La prioridad para la combinación de las configuraciones de anidamiento de archivos es: Visual Studio > Soluciones > Proyecto.

Puede indicar a Visual Studio que ignore la configuración específica de la solución y la específica del proyecto, incluso si los archivos existen en el disco. Para ello, habilite la opción **Ignorar la configuración de la solución y el proyecto** en **Herramientas** > **Opciones** > **ASP.NET Core** > **Anidamiento de archivos**.

Puede hacer lo contrario e indicar a Visual Studio que *solo* use la configuración específica de la solución o la configuración específica del proyecto. Para ello, establezca el nodo **root** en **true**. Visual Studio deja de combinar los archivos en ese nivel y no los combina con archivos que están en niveles superiores de la jerarquía.

La configuración específica de la solución y la específica del proyecto se pueden insertar en el repositorio del control de código fuente para que todo el equipo que trabaja en el código base pueda compartirlas.

## <a name="disable-file-nesting-rules-for-a-project"></a>Deshabilitación de las reglas de anidamiento de archivos para un proyecto

Las reglas de anidamiento de archivos globales existentes se pueden deshabilitar en soluciones o proyectos específicos. Basta con usar la acción **remove** en un proveedor en lugar de **add**. Por ejemplo, si agrega el siguiente código de configuración a un proyecto, se deshabilitan todas las reglas **pathSegment** que existan globalmente para este proyecto concreto:

```json
"dependentFileProviders": {
  "remove": {
    "pathSegment": {}
  }
}
```

## <a name="see-also"></a>Vea también

- [Personalizar el IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Soluciones y proyectos en Visual Studio](solutions-and-projects-in-visual-studio.md)
