---
title: 'Cómo: Localizar y organizar plantillas de proyectos y de elementos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b5f55de910eb77ec7ccbd205b78d5c95039e6b39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651871"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Cómo: Localizar y organizar plantillas de proyectos y de elementos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los archivos de plantilla se deben colocar en una ubicación que Visual Studio reconozca de forma que estas aparezcan en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento**. Puede crear subcategorías personalizadas para las plantillas de modo que estas subcategorías aparezcan también en la interfaz de usuario.

## <a name="locating-templates"></a>Buscar plantillas
 De forma predeterminada, Visual Studio busca las plantillas de proyecto y de elementos en dos ubicaciones. Si existe un archivo comprimido que incluye un archivo .vstemplate en estas ubicaciones, aparecerá una plantilla en el cuadro de diálogo **Nuevo proyecto** o **Agregar nuevo elemento**.

### <a name="installed-templates"></a>Plantillas instaladas
 De manera predeterminada, las plantillas que se instalan con el producto se encuentran en:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*Language*\\*Locale*\

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*Language*\\*Locale\\*

  Por ejemplo, el directorio siguiente contiene las plantillas de proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] correspondientes al inglés:

  C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="custom-templates"></a>Plantillas personalizadas
 De manera predeterminada, las plantillas personalizadas se encuentran en:

- \My Documents\Visual Studio *Version*\Templates\ProjectTemplates\\*Language*\

- \My Documents\Visual Studio *Version*\Templates\ItemTemplates\\*Language*\

  Por ejemplo, el directorio siguiente contiene las plantillas de proyecto personalizadas de [!INCLUDE[csprcs](../includes/csprcs-md.md)]:

  C:\Documents and Settings\UserName\My Documents\\<versión de Visual Studio\>\Templates\ProjectTemplates\Visual C#\

  Las plantillas personalizadas no incluyen un subdirectorio para las plantillas de otros idiomas. Puede cambiar el directorio predeterminado para las plantillas personalizadas en el cuadro de diálogo **Opciones**, bajo **Entorno\Proyectos y soluciones**.

## <a name="organizing-templates"></a>Organizar plantillas
 Las categorías de los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento** reflejan las estructuras de directorios que existen en las ubicaciones de plantillas instaladas y personalizadas. Puede modificar estas estructuras de directorios para organizar las plantillas de la manera que le resulte más lógica.

> [!NOTE]
> No puede crear una nueva categoría en el nivel del lenguaje de programación. Solo se pueden crear categorías nuevas dentro de cada lenguaje.

 Si las estructuras de directorios de las plantillas instaladas y personalizadas de un lenguaje en particular no son iguales (es decir, si una de las carpetas tiene directorios que no existen en la otra), el conjunto de categorías que aparecerá en el cuadro de diálogo **Nuevo proyecto** será resultado de combinar todas las categorías.

### <a name="organizing-installed-templates"></a>Organizar las plantillas instaladas
 Puede organizar las plantillas instaladas creando subdirectorios en la carpeta del lenguaje de programación. Estos subdirectorios aparecen como carpetas virtuales en los cuadros de diálogo **Nuevo proyecto** y **Agregar nuevo elemento** dentro de cada lenguaje.

##### <a name="to-create-new-installed-project-template-categories"></a>Para crear nuevas categorías de plantillas de proyecto instaladas

1. Cree una carpeta en la carpeta de lenguaje del directorio de plantillas instaladas. Por ejemplo, para crear la categoría Office para las plantillas de proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], se crearía el directorio siguiente:

    \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\

2. Coloque todas las plantillas de esta categoría en la nueva carpeta.

3. Cierre todas las instancias de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. En el menú **Inicio**, haga clic en **Ejecutar**, escriba **cmd** y haga clic en **Aceptar**.

5. En el símbolo del sistema, busque el directorio que contiene devenv.exe y escriba **devenv /installvstemplates**.

6. Ejecute [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.

8. Compruebe que la categoría Office aparece en el cuadro de diálogo **Nuevo proyecto**, en el panel **Tipos de proyecto**, bajo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].

   También puede agrupar un subconjunto de las plantillas de elementos de proyecto en una carpeta personalizada.

##### <a name="to-create-new-installed-item-template-categories"></a>Para crear nuevas categorías de plantillas de elementos instaladas

1. Cree una carpeta en la carpeta de lenguaje del directorio de plantillas instaladas. Por ejemplo, para crear la categoría Web para las plantillas de elementos de [!INCLUDE[csprcs](../includes/csprcs-md.md)], se  crearía el directorio siguiente:

     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\

2. Coloque todas las plantillas de esta categoría en la nueva carpeta.

3. Cierre todas las instancias de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. En el menú **Inicio**, haga clic en **Ejecutar**, escriba **cmd** y haga clic en **Aceptar**.

5. En el símbolo del sistema, busque el directorio que contiene devenv.exe y escriba **devenv /setup**.

6. Ejecute [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. Cree un proyecto o abra uno existente.

8. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

9. Compruebe que la categoría Web aparece en el panel **Tipos de proyecto** del cuadro de diálogo **Agregar nuevo elemento**.

### <a name="organizing-custom-templates"></a>Organizar plantillas personalizadas
 Las plantillas personalizadas se pueden organizar en sus propias categorías agregando nuevas carpetas en la ubicación de plantillas personalizadas. El cuadro de diálogo **Nuevo proyecto** refleja todos los cambios que se realizan en las categorías de plantillas.

##### <a name="to-create-new-custom-project-template-categories"></a>Para crear nuevas categorías de plantillas de proyecto personalizadas

1. Cree una carpeta en la carpeta del lenguaje del directorio de plantillas de proyecto personalizadas. Por ejemplo, para crear la categoría HelloWorld para las plantillas de [!INCLUDE[csprcs](../includes/csprcs-md.md)], crearía el directorio siguiente:

    \My Documents\\<versión de Visual Studio\>\Templates\ProjectTemplates\CSharp\HelloWorld\

2. Coloque todas las plantillas de esta categoría en la nueva carpeta.

3. En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.

4. Compruebe que la categoría HelloWorld aparece bajo [!INCLUDE[csprcs](../includes/csprcs-md.md)] en el panel **Tipos de proyecto** del cuadro de diálogo **Nuevo proyecto**.

   También puede agrupar un subconjunto de las plantillas de elementos personalizadas en una carpeta personalizada.

##### <a name="to-create-new-custom-item-template-categories"></a>Para crear nuevas categorías de plantillas de elementos personalizadas

1. Cree una carpeta en la carpeta del lenguaje en el directorio de plantillas de elementos personalizadas. Por ejemplo, para crear la categoría HelloWorld para las plantillas de [!INCLUDE[csprcs](../includes/csprcs-md.md)], se  crearía el directorio siguiente:

     \My Documents\\<versión de Visual Studio\>\Templates\ItemTemplates\CSharp\HelloWorld\

2. Coloque todas las plantillas de esta categoría en la nueva carpeta.

3. Cree un proyecto o abra uno existente.

4. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

5. Compruebe que la categoría HelloWorld aparece en el panel **Tipos de proyecto** del cuadro de diálogo **Agregar nuevo elemento**.

### <a name="displaying-templates-in-parent-categories"></a>Mostrar las plantillas de categorías primarias
 Puede permitir que las plantillas contenidas en subcategorías se muestren en sus categorías primarias utilizando el elemento `NumberOfParentCategoriesToRollUp` en el archivo .vstemplate. Estos pasos son idénticos para plantillas de proyecto y plantillas de elementos.

##### <a name="to-display-templates-in-parent-categories"></a>Para mostrar las plantillas en categorías primarias

1. Busque el archivo .zip que contiene la plantilla.

2. Extraiga el archivo .zip.

3. Abra el archivo .vstemplate en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. En el elemento `TemplateData`, agregue un elemento `NumberOfParentCategoriesToRollUp`. Por ejemplo, el código siguiente hace que la plantilla esté visible en la categoría primaria, pero no en los niveles superiores.

    ```
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

5. Guarde y cierre el archivo .vstemplate.

6. Seleccione los archivos de la plantilla, haga clic con el botón derecho en la selección, haga clic en **Enviar a** y, después, en **Carpetas comprimidas (en zip)** . Los archivos se comprimen en un archivo .zip.

7. Elimine los archivos de plantilla extraídos y el archivo .zip de plantilla antiguo.

8. Coloque el nuevo archivo .zip en el directorio que contenía el archivo .zip eliminado.

## <a name="see-also"></a>Vea también
 [Personalizar plantillas plantillas de](../ide/customizing-project-and-item-templates.md) [Visual Studio referencia de esquema](../extensibility/visual-studio-template-schema-reference.md) de plantillas [NumberOfParentCategoriesToRollUp (plantillas de Visual Studio)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) [Cómo: crear plantillas de proyecto](../ide/how-to-create-project-templates.md) [Cómo: crear plantillas de elementos](../ide/how-to-create-item-templates.md)
