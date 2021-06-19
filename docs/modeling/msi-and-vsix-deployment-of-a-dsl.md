---
title: Implementación mediante MSI y VSIX de un DSL
description: Obtenga información sobre cómo puede instalar un lenguaje específico de dominio (DSL) en su propio equipo o en otros equipos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 879028746eac10160492f03651ef8b51714e9c6a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391015"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Implementación mediante MSI y VSIX de un DSL
Puede instalar un lenguaje específico del dominio en su propio equipo o en otros equipos. Visual Studio debe estar instalado en el equipo de destino.

## <a name="choosing-between-vsix-and-msi-deployment"></a><a name="which"></a> Elección entre vsix e implementación de MSI
 Hay dos métodos para implementar un lenguaje específico de dominio:

|Método|Ventajas|
|-|-|
|VSX (Visual Studio extensión)|Muy fácil de implementar: copie y ejecute el **archivo .vsix** desde el proyecto DslPackage.<br /><br /> Para obtener más [información, vea Installing and Uninstalling a DSL by using the VSX](#Installing).|
|MSI (archivo del instalador)|: permite al usuario abrir Visual Studio haciendo doble clic en un archivo DSL.<br />- Asocia un icono con el tipo de archivo DSL en el equipo de destino.<br />- Asocia un XSD (esquema XML) con el tipo de archivo DSL. Esto evita advertencias cuando el archivo se carga en Visual Studio.<br /><br /> Debe agregar un proyecto de instalación a la solución para crear una MSI.<br /><br /> Para obtener más información, consulte [Implementación de un DSL mediante un archivo MSI.](#msi)|

## <a name="install-and-uninstall-a-dsl-by-using-the-vsx"></a><a name="Installing"></a> Instalación y desinstalación de un DSL mediante VSX

Cuando el DSL se instala mediante este método, el usuario puede abrir un archivo DSL desde dentro de Visual Studio, pero el archivo no se puede abrir desde Explorador de Windows.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Para instalar un DSL mediante VSX

1. Busque el **archivo .vsix** creado por el proyecto de paquete DSL:

   1. En **Explorador de soluciones**, haga clic con el botón derecho en **el proyecto DslPackage** y, a continuación, haga clic en Abrir carpeta **Explorador de archivos**.

   2. Busque el contenedor **de archivos \\ \* \\**_YourProject_**. DslPackage.vsix**

2. Copie el **archivo .vsix** en el equipo de destino en el que desea instalar el DSL. Puede tratarse de su propio equipo o de otro.

   - El equipo de destino debe tener una de las ediciones de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] que admiteNSL en tiempo de ejecución. Para obtener más información, vea [Supported Visual Studio Editions for Visualization & Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - El equipo de destino debe tener una de las ediciones de Visual Studio especificadas en **DslPackage\source.extensions.manifest**.

3. En el equipo de destino, haga doble clic en **el archivo .vsix.**

    El **Instalador de extensiones de Visual Studio** se abre e instala la extensión.

4. Inicie o reinicie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5. Para probar el DSL, use Visual Studio para crear un nuevo archivo que tenga la extensión que definió para el DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Para desinstalar un DSL que se instaló mediante VSX

1. En el menú **Herramientas** , elija **Extensiones y actualizaciones**.

2. Expanda **Extensiones instaladas**.

3. Seleccione la extensión en la que se define el DSL y, a continuación, haga clic en **Desinstalar**.

   En contadas ocasiones, una extensión defectuosa no se carga y crea un informe en la ventana de error, aunque no aparece en el Administrador de extensiones. En ese caso, puede quitar la extensión eliminando el archivo de:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="deploying-a-dsl-in-an-msi"></a><a name="msi"></a> Implementación de un DSL en una MSI
 Al definir un archivo MSI (Windows Installer) para el DSL, puede permitir que los usuarios abran archivos DSL desde Explorador de Windows. También puede asociar un icono y una breve descripción a la extensión de nombre de archivo. Además, msi puede instalar un XSD que se puede usar para validar archivos DSL. Si lo desea, puede agregar otros componentes a msi que se instalarán al mismo tiempo.

 Para obtener más información sobre los archivos MSI y otras opciones de implementación, vea [Implementación de aplicaciones, servicios y componentes.](../deployment/deploying-applications-services-and-components.md)

 Para compilar una MSI, agregue un proyecto de instalación a la Visual Studio solución. El método más sencillo para crear un proyecto de instalación es usar la plantilla CreateMsiSetupProject.tt, que puede descargar desde el [sitio de VMSDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

### <a name="to-deploy-a-dsl-in-an-msi"></a>Para implementar un DSL en una MSI

1. Establezca `InstalledByMsi` en el manifiesto de extensión. Esto evita que VSX se instale y desinstale, excepto por msi. Esto es importante si va a incluir otros componentes en msi.

   1. Abra DslPackage\source.extension.tt

   2. Inserte la siguiente línea antes de `<SupportedProducts>` :

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Cree o edite un icono que represente el DSL en Explorador de Windows. Por ejemplo, edite **DslPackage\Resources\File.ico.**

3. Asegúrese de que los siguientes atributos del DSL son correctos:

   - En el Explorador de DSL, haga clic en el nodo raíz y, en ventana Propiedades, revise:

       - Descripción

       - Versión

   - Haga clic en **el nodo Editor** y, en la ventana Propiedades, haga clic en **Icono**. Establezca el valor para hacer referencia a un archivo de icono **en DslPackage\Resources,** como **File.ico.**

   - En el **menú Compilar,** abra **Administrador de configuración** y seleccione la configuración que desea compilar, como **Liberar o** **Depurar**.

4. Vaya a la [página principal del SDK de visualización](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)y modelado y, en la pestaña Descargas, descargue **CreateMsiSetupProject.tt**. 

5. Agregue **CreateMsiSetupProject.tt** al proyecto dsl.

    Visual Studio creará un archivo denominado **CreateMsiSetupProject.vdproj**.

6. En Explorador de Windows, copie Dsl \\ *.vdproj en una nueva carpeta denominada Setup.

    (Si lo desea, ahora puede excluir CreateMsiSetupProject.tt del proyecto dsl).

7. En **Explorador de soluciones**, agregue **el archivo \\ \* .vdproj del programa** de instalación como un proyecto existente.

8. En el menú **Proyecto** , haga clic en **Dependencias del proyecto**.

    En el cuadro **de diálogo Dependencias** del proyecto, seleccione el proyecto de instalación.

    Seleccione el cuadro situado junto a **DslPackage**.

9. Recompilar la solución.

10. En Explorador de Windows, busque el archivo MSI creado en el proyecto de instalación.

     Copie el archivo MSI en un equipo en el que quiera instalar el DSL. Haga doble clic en el archivo MSI. El instalador se ejecuta.

11. En el equipo de destino, cree un nuevo archivo que tenga la extensión de archivo del DSL. Compruebe lo siguiente:

    - En Explorador de Windows vista de lista, el archivo aparece con el icono y la descripción que ha definido.

    - Al hacer doble clic en el archivo, Visual Studio inicia y abre el archivo DSL en el editor DSL.

    Si lo prefiere, puede crear el proyecto de instalación manualmente, en lugar de usar la plantilla de texto. Para ver un tutorial que incluya este procedimiento, consulte el capítulo 5 del laboratorio del SDK de visualización [y modelado](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207).

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Para desinstalar un DSL que se instaló desde una MSI

1. En Windows, abra el panel de control **Programas y** características.

2. Desinstale el DSL.

3. Reinicie Visual Studio.
