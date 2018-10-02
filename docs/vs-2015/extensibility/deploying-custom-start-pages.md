---
title: Implementación de las páginas de inicio personalizada | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a7c4ec55263212ef7c44c7e5b6093ef4a3e9adb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578357"
---
# <a name="deploying-custom-start-pages"></a>Implementación de páginas de inicio personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Deploying Custom Start Pages](https://docs.microsoft.com/visualstudio/extensibility/deploying-custom-start-pages).  
  
Puede implementar páginas principales personalizadas mediante la implementación de VSIX o copiando los archivos en las ubicaciones correctas en el equipo de destino.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Implementación de VSIX mediante el uso de la plantilla de proyecto de página de inicio  
 Al crear una página de inicio mediante el uso de la plantilla de proyecto de la página de inicio y, a continuación, compile el proyecto, Visual Studio crea un archivo .vsix que se puede distribuir. Empaquetado de una página de inicio en un archivo .vsix le ofrece las siguientes opciones para la implementación, dependiendo de la audiencia prevista:  
  
-   Puede colocar el archivo .vsix en un recurso compartido de red o en un sitio Web público. Cuando el archivo se abre la página de inicio se instala automáticamente.  
  
-   Puede cargar el archivo .vsix en el [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) del sitio Web para que los usuarios pueden instalar mediante el uso de **Administrador de extensiones**.  
  
 La plantilla de proyecto de la página de inicio crea una copia de la página de inicio de Visual Studio de forma predeterminada para que pueda modificar la copia y conservar el original.  
  
 Puede obtener la plantilla de proyecto de la página de inicio mediante **Administrador de extensiones** o descargándolo desde el sitio Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Implementación de VSIX sin usar la plantilla de proyecto de página de inicio  
 Una implementación correcta de VSIX requiere una extensión para instalarse en carpetas que son reconocidas por el proceso de registro VSIX y por **Administrador de extensiones**. Puesto que la plantilla de proyecto de la página de inicio ya especifica las carpetas correctas, se recomienda usar siempre que quiera empaquetar una extensión para la implementación de VSIX. Sin embargo, si tiene un caso en el que no se puede usar la plantilla, puede crear una implementación de VSIX sin usarlo.  
  
 Para crear una implementación de VSIX sin usar la plantilla de proyecto de la página de inicio, en primer lugar, cree un archivo .vsix para la página de inicio de cualquiera de estas dos maneras:  
  
-   Mediante la adición de los archivos de la página de inicio personalizados a un proyecto de VSIX vacío. Para obtener más información, consulte [plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).  
  
-   Al crear manualmente un archivo .vsix. Para obtener más información, consulte [Cómo: empaquetar manualmente una extensión (implementación VSIX)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
 Para Visual Studio reconocer una página de inicio, la `Content Element` de manifiesto de VSIX debe contener un `CustomExtension Element` que tiene el `Type` atributo establecido en `"StartPage"`. Aparece una extensión de la página de inicio que se ha instalado mediante la implementación de VSIX en el **Personalizar página principal** lista el **inicio** opciones de página como **[instalado la extensión]** *Nombre de la extensión*.  
  
 Si el paquete de la página de inicio incluye los ensamblados, debe agregar el registro de la ruta de acceso de enlace para que estén disponibles cuando se inicia Visual Studio. Para ello, asegúrese de que el paquete incluye un archivo .pkgdef que tiene la siguiente información.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Implementación de VSIX para todos los usuarios  
 De forma predeterminada, las extensiones implementadas en paquetes VSIX se instalan solo para el usuario actual. Puede realizar una instalación de la página de inicio para todos los usuarios de la máquina de destino mediante la creación de una implementación de todos los usuarios.  
  
##### <a name="to-create-an-all-users-deployment"></a>Para crear una implementación de todos los usuarios  
  
1.  Abra el archivo extension.vsixmanifest en la vista código.  
  
2.  En el `Identifier` elemento del manifiesto de vsix, agregue un `AllUsers` elemento que tiene un valor de `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Esto hace que el instalador de vsix solicitar permisos de administrador y, a continuación, instalar los archivos en \common7\ide\extensions\.  
  
3.  Abra el archivo .pkgdef.  
  
4.  Modificar el .pkgdef para establecer la página de inicio predeterminado en HKLM agregando lo siguiente, donde *MyStartPage.xaml* es el nombre del archivo .xaml que contiene la página de inicio.  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"  
  
     Esto indica a Visual predominante para buscar en la nueva ubicación de la página de inicio.  
  
## <a name="file-copy-deployment"></a>Implementación de copia de archivos  
 No es necesario que crear un archivo .vsix para implementar una página de inicio personalizada. En su lugar, puede copiar los archivos auxiliares y el marcado directamente en la carpeta del usuario \StartPages\. El **Personalizar página principal** lista el **inicio** página de opciones enumera todos los archivos .xaml en esa carpeta, junto con la ruta de acceso — por ejemplo, %USERPROFILE%\My Documents\Visual Studio  *versión*\StartPages\\*nombre de archivo*.xaml. Si la página de inicio incluye referencias a ensamblados privados, debe copiarlos y pegarlos en la carpeta \PrivateAssemblies\.  
  
 Para distribuir una página de inicio que se crea sin empaquetado en un archivo .vsix, recomendamos que use una estrategia de copia de archivo básico, por ejemplo, un script por lotes o cualquier otra tecnología de implementación que le permite coloca los archivos en los directorios necesarios.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Para instalar manualmente una página de inicio personalizada  
  
1.  Copie el archivo .xaml que contiene el marcado de página de inicio, junto con todos los archivos auxiliares que no sean ensamblados y péguelos en la carpeta del usuario \StartPages\.  
  
2.  Si la página de inicio requiere ensamblados, cópielos y péguelos en... \\ *Carpeta de instalación de visual Studio*\Common7\IDE\PrivateAssemblies\\.  
  
3.  En el **Personalizar página principal** lista el **inicio** opciones, seleccione la nueva página de inicio. Para obtener más información, consulte [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la página principal](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Adición de control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)

