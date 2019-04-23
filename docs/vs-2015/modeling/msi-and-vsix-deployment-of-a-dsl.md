---
title: Implementación mediante MSI y VSIX de un DSL | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6ce16f06-1978-4e19-8cdc-441ee65a3fb2
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3aaaf704e1ad8880ef7768ef9d7a23d325882a15
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60094443"
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Implementación mediante MSI y VSIX de un DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede instalar un idioma específico de dominio en su propio equipo o en otros equipos. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ya debe instalarse en el equipo de destino.  
  
## <a name="which"></a> Elegir entre la implementación de MSI y VSIX  
 Hay dos métodos para implementar un lenguaje específico de dominio:  
  
|Método|Ventajas|  
|------------|--------------|  
|VSX ([!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensión)|Muy fácil de implementar: Copie y ejecute el **.vsix** archivo desde el proyecto DslPackage.<br /><br /> Para obtener más información, consulte [instalación y desinstalación de un DSL mediante el uso de la VSX](#Installing).|  
|MSI (archivo de instalador)|: Permite al usuario que abra [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] haciendo doble clic en un archivo DSL.<br />-Un icono se asocia con el tipo de archivo DSL en el equipo de destino.<br />-Un XSD (esquema XML) se asocia con el tipo de archivo DSL. Esto evita las advertencias cuando se carga el archivo en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].<br /><br /> Debe agregar un proyecto de instalación a la solución para crear un archivo MSI.<br /><br /> Para obtener más información, consulte [implementar un DSL mediante un archivo MSI](#msi).|  
  
## <a name="Installing"></a> Instalación y desinstalación de un DSL mediante el uso de la VSX  
 Cuando este método instala su DSL, el usuario puede abrir un archivo DSL desde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], pero no se puede abrir el archivo desde el Explorador de Windows.  
  
#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Para instalar un DSL con la VSX  
  
1. En el equipo, busque el **.vsix** archivo que se compila el proyecto de paquete de DSL.  
  
    1. En **el Explorador de soluciones**, haga clic en el **DslPackage** del proyecto y, a continuación, haga clic en **Abrir carpeta en el Explorador de Windows**.  
  
    2. Busque el archivo **bin\\\*\\**_convertirá_**. DslPackage.vsix**  
  
2. Copia el **.vsix** archivo al equipo de destino en el que desea instalar el DSL. Puede tratarse de su propio equipo o de otro.  
  
    - El equipo de destino debe tener una de las ediciones de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que admite lenguajes DSL en tiempo de ejecución. Para obtener más información, consulte [admite ediciones de Microsoft Visual Studio de visualización y el SDK de modelado](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).  
  
    - El equipo de destino debe tener una de las ediciones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] especificado en **DslPackage\source.extensions.manifest**.  
  
3. En el equipo de destino, haga doble clic en el **.vsix** archivo.  
  
     El**Instalador de extensiones de Visual Studio** se abre e instala la extensión.  
  
4. Inicie o reinicie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
5. Para probar el DSL, use [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para crear un nuevo archivo que tenga la extensión que ha definido para su DSL.  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Para desinstalar un DSL que se instaló mediante el uso de VSX  
  
1. En el **herramientas** menú, haga clic en **Administrador de extensiones**.  
  
2. Expanda **Extensiones instaladas**.  
  
3. Seleccione la extensión en el que se define el DSL y, a continuación, haga clic en **desinstalar**.  
  
   En contadas ocasiones, una extensión defectuosa no se carga y crea un informe en la ventana de error, aunque no aparece en el Administrador de extensiones. En ese caso, puede quitar la extensión eliminando el archivo de:  
  
   *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**  
  
## <a name="msi"></a> Implementar un DSL en un archivo MSI  
 Mediante la definición de un archivo MSI (Windows Installer) para su DSL, puede permitir a los usuarios abrir archivos DSL desde el Explorador de Windows. También puede asociar un icono y una descripción breve con la extensión de nombre de archivo. Además, el archivo MSI puede instalar un XSD que se puede usar para validar los archivos de DSL. Si lo desea, puede agregar otros componentes en el archivo MSI que se instala al mismo tiempo.  
  
 Para obtener más información acerca de los archivos MSI y otras opciones de implementación, consulte [implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md).  
  
 Para generar un archivo MSI, agrega un proyecto de instalación para su [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] solución. El método más fácil de crear un proyecto de instalación consiste en usar la plantilla CreateMsiSetupProject.tt, que puede descargar desde el [sitio VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).  
  
#### <a name="to-deploy-a-dsl-in-an-msi"></a>Para implementar un DSL en un archivo MSI  
  
1. Establecer `InstalledByMsi` en el manifiesto de la extensión. Esto impide que la VSX se instalan y desinstalan, excepto por el archivo MSI. Esto es importante si va a incluir otros componentes en el archivo MSI.  
  
   1. Abra DslPackage\source.extension.tt  
  
   2. Inserte la línea siguiente antes de `<SupportedProducts>`:  
  
       ```  
       <InstalledByMsi>true</InstalledByMsi>  
       ```  
  
2. Crear o editar un icono que represente su DSL en el Explorador de Windows. Por ejemplo, editar **DslPackage\Resources\File.ico**  
  
3. Asegúrese de que los siguientes atributos de su DSL son correctos:  
  
   - En el Explorador de DSL, haga clic en el nodo raíz y, en la ventana Propiedades, revise:  
  
       - Descripción  
  
       - Versión  
  
   - Haga clic en el **Editor** nodo y haga clic en la ventana Propiedades, **icono**. Establezca el valor para hacer referencia a un archivo de icono en **DslPackage\Resources**, tales como **File.ico**  
  
   - En el **compilar** menú Abrir **Configuration Manager**y seleccione la configuración que desea crear, como **versión** o **depurar** .  
  
4. Vaya a [página principal de SDK de visualización y modelado](http://go.microsoft.com/fwlink/?LinkID=186128)y desde el **descargas** pestaña, descargue **CreateMsiSetupProject.tt**.  
  
5. Agregar **CreateMsiSetupProject.tt** a su proyecto de Dsl.  
  
    [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se creará un archivo denominado **CreateMsiSetupProject.vdproj**.  
  
6. En el Explorador de Windows, copie Dsl\\\*.vdproj a una carpeta nueva denominada el programa de instalación.  
  
    (Si lo desea, puede ahora excluir CreateMsiSetupProject.tt desde el proyecto de Dsl).  
  
7. En **el Explorador de soluciones**, agregar **instalación\\\*.vdproj** como un proyecto existente.  
  
8. En el **proyecto** menú, haga clic en **dependencias del proyecto**.  
  
    En el **dependencias del proyecto** cuadro de diálogo, seleccione el proyecto de instalación.  
  
    Active la casilla junto a **DslPackage**.  
  
9. Recompilar la solución.  
  
10. En el Explorador de Windows, busque el archivo MSI generado en el proyecto de instalación.  
  
     Copie el archivo MSI en un equipo en el que desea instalar su DSL. Haga doble clic en el archivo MSI. Se ejecuta el programa de instalación.  
  
11. En el equipo de destino, cree un nuevo archivo que tiene la extensión de archivo de su DSL. Compruebe lo siguiente:  
  
    - En la vista de lista del explorador de Windows, el archivo aparece con el icono y la descripción que ha definido.  
  
    - Al hacer doble clic en el archivo, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se inicia y se abre el archivo DSL en el editor de DSL.  
  
    Si lo prefiere, puede crear el proyecto de instalación manualmente, en lugar de usar la plantilla de texto. Para ver un tutorial que incluye este procedimiento consulte el capítulo 5 de la [de visualización y modelado SDK laboratorio](http://go.microsoft.com/fwlink/?LinkId=208878).  
  
#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Para desinstalar un DSL que se instaló desde un archivo MSI  
  
1. En Windows, abra el **programas y características** panel de control.  
  
2. Desinstale el DSL.  
  
3. Reinicie Visual Studio.
