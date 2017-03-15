---
title: "MSI y la implementación de VSIX de un DSL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 2
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: beb505dca6f5b52046ca87e854260f4b222079c8
ms.lasthandoff: 02/22/2017

---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Implementación mediante MSI y VSIX de un DSL
Puede instalar un lenguaje específico de dominio en su propio equipo o en otros equipos. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ya debe instalarse en el equipo de destino.  
  
##  <a name="a-namewhicha-choosing-between-vsix-and-msi-deployment"></a><a name="which"></a>Elegir entre la implementación de MSI y VSIX  
 Existen dos métodos de implementación de un lenguaje específico de dominio:  
  
|Método|Ventajas|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] extensión)|Muy fácil de implementar: copiar y ejecutar el **.vsix** archivo desde el proyecto DslPackage.<br /><br /> Para obtener más información, consulte [instalar y desinstalar un DSL utilizando la VSX](#Installing).|  
|MSI (archivo de instalador)|: Permite al usuario abrir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] haciendo doble clic en un archivo DSL.<br />-Asocia un icono con el tipo de archivo DSL en el equipo de destino.<br />-Asocia un XSD (esquema XML) con el tipo de archivo DSL. Esto evita advertencias cuando se carga el archivo en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> Debe agregar un proyecto de instalación a la solución para crear un archivo MSI.<br /><br /> Para obtener más información, consulte [implementar un DSL mediante un archivo MSI](#msi).|  
  
##  <a name="a-nameinstallinga-installing-and-uninstalling-a-dsl-by-using-the-vsx"></a><a name="Installing"></a>Instalación y desinstalación de un DSL utilizando la VSX  
 Cuando su DSL se instala mediante este método, el usuario puede abrir un archivo DSL desde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], pero no se puede abrir el archivo desde el Explorador de Windows.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Para instalar un DSL con la VSX  
  
1.  En el equipo, busque la **.vsix** archivo que se creó el proyecto de paquete de DSL.  
  
    1.  En **el Explorador de soluciones**, haga clic en el **DslPackage** del proyecto y, a continuación, haga clic en **Abrir carpeta en el Explorador de Windows**.  
  
    2.  Locate the file **bin\\\*\\***YourProject***. DslPackage.vsix**  
  
2.  Copia la **.vsix** archivos en el equipo de destino en el que desea instalar el DSL. Puede tratarse de su propio equipo o de otro.  
  
    -   El equipo de destino debe tener una de las ediciones de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] que admite los lenguajes DSL en tiempo de ejecución. Para obtener más información, consulte [admite ediciones de Microsoft Visual Studio para SDK de modelado de aspecto de visualización](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    -   El equipo de destino debe tener una de las ediciones de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] especificado en **DslPackage\source.extensions.manifest**.  
  
3.  En el equipo de destino, haga doble clic en el **.vsix** archivo.  
  
     El**Instalador de extensiones de Visual Studio** se abre e instala la extensión.  
  
4.  Inicie o reinicie [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
5.  Para probar el DSL, use [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para crear un nuevo archivo que tenga la extensión que ha definido para su DSL.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Para desinstalar un DSL que se instaló mediante VSX  
  
1.  En el **herramientas** menú, haga clic en **Administrador de extensiones**.  
  
2.  Expanda **Extensiones instaladas**.  
  
3.  Seleccione la extensión en el que se define el DSL y, a continuación, haga clic en **desinstalar**.  
  
 En contadas ocasiones, una extensión defectuosa no se carga y crea un informe en la ventana de error, aunque no aparece en el Administrador de extensiones. En ese caso, puede quitar la extensión eliminando el archivo de:  
  
 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
##  <a name="a-namemsia-deploying-a-dsl-in-an-msi"></a><a name="msi"></a>Implementar un DSL en MSI  
 Al definir un archivo MSI (Windows Installer) para su DSL, puede permitir a los usuarios abrir archivos DSL desde el Explorador de Windows. También puede asociar un icono y una descripción breve con la extensión de nombre de archivo. Además, el archivo MSI puede instalar un XSD que se puede utilizar para validar los archivos DSL. Si lo desea, puede agregar otros componentes en el archivo MSI que se instalen al mismo tiempo.  
  
 Para obtener más información acerca de los archivos MSI y otras opciones de implementación, consulte [implementación de aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md).  
  
 Para generar un archivo MSI, se agrega un proyecto de instalación para su [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución. El método más fácil de crear un proyecto de instalación es utilizar la plantilla CreateMsiSetupProject.tt, que puede descargar desde el [sitio VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Para implementar un DSL en MSI  
  
1.  Establecer `InstalledByMsi` en el manifiesto de la extensión. Esto evita que la VSX se instalan y desinstalan excepto el MSI. Esto es importante si va a incluir otros componentes en el archivo MSI.  
  
    1.  Abra DslPackage\source.extension.tt  
  
    2.  Inserte la siguiente línea antes de `<SupportedProducts>`:  
  
        ```  
        <InstalledByMsi>true</InstalledByMsi>  
        ```  
  
2.  Crear o editar un icono que representa su DSL en el Explorador de Windows. Por ejemplo, editar **DslPackage\Resources\File.ico**  
  
3.  Asegúrese de que los siguientes atributos del ADSL son correctos:  
  
    -   Haga clic en el nodo raíz en el Explorador de DSL y en la ventana Propiedades, revise:  
  
        -   Descripción  
  
        -   Versión  
  
    -   Haga clic en el **Editor** nodo y en la ventana Propiedades, haga clic en **icono**. Establezca el valor para hacer referencia a un archivo de icono en **DslPackage\Resources**, como **File.ico**  
  
    -   En el **crear** menú Abrir **Configuration Manager**y seleccione la configuración que desea crear, como **versión** o **depurar**.  
  
4.  Vaya a [página principal de SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=186128)y desde el **descargas** ficha, descargue **CreateMsiSetupProject.tt**.  
  
5.  Agregar **CreateMsiSetupProject.tt** a su proyecto de Dsl.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]se creará un archivo denominado **CreateMsiSetupProject.vdproj**.  
  
6.  En el Explorador de Windows, copie Dsl\\*.vdproj a una nueva carpeta denominada Setup.  
  
     (Si lo desea, puede ahora excluir CreateMsiSetupProject.tt de su proyecto de Dsl).  
  
7.  En **el Explorador de soluciones**, agregue **instalación\\\*.vdproj** como un proyecto existente.  
  
8.  En el **proyecto** menú, haga clic en **dependencias del proyecto**.  
  
     En el **dependencias del proyecto** cuadro de diálogo, seleccione el proyecto de instalación.  
  
     Active la casilla junto a **DslPackage**.  
  
9. Recompilar la solución.  
  
10. En el Explorador de Windows, busque el archivo MSI generado en su proyecto de instalación.  
  
     Copie el archivo MSI en un equipo en el que desea instalar el DSL. Haga doble clic en el archivo MSI. Se ejecuta el programa de instalación.  
  
11. En el equipo de destino, cree un nuevo archivo que tiene la extensión de archivo de su DSL. Compruebe que:  
  
    -   En la vista de lista del explorador de Windows, el archivo aparece con el icono y la descripción que ha definido.  
  
    -   Cuando haga doble clic en el archivo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se inicia y se abre el archivo DSL en el editor de DSL.  
  
 Si lo prefiere, puede crear el proyecto de instalación manualmente, en lugar de usar la plantilla de texto. Para obtener un tutorial que incluye este procedimiento consulte el capítulo 5 de la [de visualización y modelado de SDK de laboratorio](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Para desinstalar un DSL que se instaló desde un archivo MSI  
  
1.  En Windows, abra la **programas y características** panel de control.  
  
2.  Desinstale el DSL.  
  
3.  Reinicie Visual Studio.
