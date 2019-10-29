---
title: Implementación mediante MSI y VSIX de un DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73c81d88f055ea7a585e3d14ab4a0086d9236938
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984447"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Implementación mediante MSI y VSIX de un DSL
Puede instalar un lenguaje específico de dominio en su propio equipo o en otros equipos. Visual Studio ya debe estar instalado en el equipo de destino.

## <a name="which"></a>Elección entre la implementación de VSIX y MSI
 Existen dos métodos para implementar un lenguaje específico de dominio:

|Método|Ventajas|
|-|-|
|VSX (extensión de Visual Studio)|Muy fácil de implementar: Copie y ejecute el archivo **. vsix** del proyecto DslPackage.<br /><br /> Para obtener más información [, consulte Instalación y desinstalación de DSL mediante el uso de VSX](#Installing).|
|MSI (archivo del instalador)|: Permite al usuario abrir Visual Studio haciendo doble clic en un archivo DSL.<br />-Asocia un icono con el tipo de archivo DSL en el equipo de destino.<br />-Asocia un XSD (esquema XML) con el tipo de archivo DSL. Esto evita advertencias cuando el archivo se carga en Visual Studio.<br /><br /> Debe agregar un proyecto de instalación a la solución para crear un MSI.<br /><br /> Para obtener más información, consulte [implementación de un DSL mediante un archivo MSI](#msi).|

## <a name="Installing"></a>Instalación y desinstalación de DSL mediante el uso de VSX

Cuando este método instala DSL, el usuario puede abrir un archivo DSL desde Visual Studio, pero el archivo no se puede abrir desde el explorador de Windows.

### <a name="to-install-a-dsl-by-using-the-vsx"></a>Para instalar un DSL mediante el uso de VSX

1. Busque el archivo **. vsix** compilado por el proyecto de paquete DSL:

   1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto **DslPackage** y, a continuación, haga clic en **Abrir carpeta en el explorador de archivos**.

   2. Busque el archivo **\\ \* \\** _YourProject_ **. DslPackage. vsix**

2. Copie el archivo **. vsix** en el equipo de destino en el que desea instalar el DSL. Puede tratarse de su propio equipo o de otro.

   - El equipo de destino debe tener una de las ediciones de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] que admita DSL en tiempo de ejecución. Para obtener más información, consulte las [ediciones de Visual Studio compatibles con el SDK de modelado de & de visualización](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

   - El equipo de destino debe tener una de las ediciones de Visual Studio especificadas en **DslPackage\source.Extensions.manifest**.

3. En el equipo de destino, haga doble clic en el archivo **. vsix** .

    El**Instalador de extensiones de Visual Studio** se abre e instala la extensión.

4. Inicie o reinicie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5. Para probar el DSL, use Visual Studio para crear un nuevo archivo que tenga la extensión que definió para el DSL.

### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Para desinstalar un DSL que se instaló con VSX

1. En el menú **Herramientas** , elija **Extensiones y actualizaciones**.

2. Expanda **Extensiones instaladas**.

3. Seleccione la extensión en la que se define el DSL y, a continuación, haga clic en **desinstalar**.

   En contadas ocasiones, una extensión defectuosa no se carga y crea un informe en la ventana de error, aunque no aparece en el Administrador de extensiones. En ese caso, puede quitar la extensión eliminando el archivo de:

   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

## <a name="msi"></a>Implementación de un DSL en un archivo MSI
 Al definir un archivo MSI (Windows Installer) para el DSL, puede permitir que los usuarios abran archivos DSL desde el explorador de Windows. También puede asociar un icono y una breve descripción a la extensión de nombre de archivo. Además, el MSI puede instalar un XSD que se puede usar para validar archivos DSL. Si lo desea, puede agregar otros componentes en el archivo MSI que se instalarán al mismo tiempo.

 Para obtener más información acerca de los archivos MSI y otras opciones de implementación, vea [implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md).

 Para compilar una MSI, agregue un proyecto de instalación a la solución de Visual Studio. El método más fácil de crear un proyecto de instalación es usar la plantilla CreateMsiSetupProject.tt, que se puede descargar desde el [sitio VMSDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).

### <a name="to-deploy-a-dsl-in-an-msi"></a>Para implementar un DSL en un archivo MSI

1. Establezca `InstalledByMsi` en el manifiesto de la extensión. Esto evita que el VSX se instale y desinstale excepto por el MSI. Esto es importante si va a incluir otros componentes en el MSI.

   1. Abrir DslPackage\source.extension.tt

   2. Inserte la siguiente línea antes de `<SupportedProducts>`:

       ```xml
       <InstalledByMsi>true</InstalledByMsi>
       ```

2. Cree o edite un icono que represente el DSL en el explorador de Windows. Por ejemplo, Edit **DslPackage\Resources\File.ico**

3. Asegúrese de que los siguientes atributos de DSL son correctos:

   - En el explorador de DSL, haga clic en el nodo raíz y, en ventana Propiedades, revise:

       - Descripción

       - Versión

   - Haga clic en el nodo **Editor** y, en el ventana Propiedades, haga clic en **icono**. Establezca el valor para que haga referencia a un archivo de icono en **DslPackage\Resources**, como **archivo. ico.**

   - En el menú **compilar** , Abra **Configuration Manager**y seleccione la configuración que desea compilar, como **liberar** o **depurar**.

4. Vaya a la [Página principal del SDK de visualización y modelado](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)y, en la pestaña **descargas** , descargue **CreateMsiSetupProject.TT**.

5. Agregue **CreateMsiSetupProject.TT** al proyecto DSL.

    Visual Studio creará un archivo denominado **CreateMsiSetupProject. vdproj**.

6. En el explorador de Windows, copie DSL \\ *. vdproj en una nueva carpeta denominada Setup.

    (Si lo desea, ahora puede excluir CreateMsiSetupProject.tt del proyecto DSL).

7. En **Explorador de soluciones**, agregue el **programa de instalación \\ \*. vdproj** como un proyecto existente.

8. En el menú **proyecto** , haga clic en **dependencias del proyecto**.

    En el cuadro de diálogo **dependencias del proyecto** , seleccione el proyecto de instalación.

    Active la casilla situada junto a **DslPackage**.

9. Recompilar la solución.

10. En el explorador de Windows, busque el archivo MSI compilado en el proyecto de instalación.

     Copie el archivo MSI en un equipo en el que desee instalar el DSL. Haga doble clic en el archivo MSI. El instalador se ejecuta.

11. En el equipo de destino, cree un nuevo archivo que tenga la extensión de archivo de su DSL. Compruebe que:

    - En la vista de lista del explorador de Windows, el archivo aparece con el icono y la descripción que ha definido.

    - Al hacer doble clic en el archivo, Visual Studio se inicia y abre el archivo DSL en el editor de DSL.

    Si lo prefiere, puede crear el proyecto de instalación manualmente, en lugar de usar la plantilla de texto. Para ver un tutorial que incluye este procedimiento, consulte el capítulo 5 del [laboratorio SDK de visualización y modelado](https://code.msdn.microsoft.com/DSLToolsLab/Release/ProjectReleases.aspx?ReleaseId=4207).

### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Para desinstalar un DSL que se instaló desde un archivo MSI

1. En Windows, abra el panel de control **programas y características** .

2. Desinstale el DSL.

3. Reinicie Visual Studio.