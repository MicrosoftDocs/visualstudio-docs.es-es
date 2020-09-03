---
title: Implementación de páginas de inicio personalizadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1cdd172c2960024da8b12735764161d36498c4e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162105"
---
# <a name="deploying-custom-start-pages"></a>Implementación de páginas de inicio personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede implementar páginas de inicio personalizadas mediante la implementación de VSIX o copiando los archivos en las ubicaciones correctas en el equipo de destino.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Implementación de VSIX mediante la plantilla de proyecto de página de inicio  
 Al crear una página de inicio mediante la plantilla de proyecto de página de inicio y, a continuación, compilar el proyecto, Visual Studio crea un archivo. vsix que se puede distribuir. Al empaquetar una página de inicio en un archivo. vsix, se proporcionan las siguientes opciones para la implementación, según el público previsto:  
  
- Puede colocar el archivo. vsix en un recurso compartido de red o en un sitio web público. Cuando alguien Abra el archivo, la página de inicio se instalará automáticamente.  
  
- Puede cargar el archivo. vsix en el sitio web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para que los usuarios puedan instalarlo mediante el **Administrador de extensiones**.  
  
  La plantilla de proyecto de página de inicio crea una copia de la página de inicio predeterminada de Visual Studio para que pueda modificar la copia y conservar el original.  
  
  Puede obtener la plantilla de proyecto de la página de inicio con el **Administrador de extensiones** o mediante su descarga desde el sitio Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Implementación de VSIX sin usar la plantilla de proyecto de página de inicio  
 Una implementación de VSIX correcta requiere la instalación de una extensión en las carpetas reconocidas por el proceso de registro de VSIX y por el **Administrador de extensiones**. Dado que la plantilla de proyecto de página de inicio ya especifica las carpetas correctas, se recomienda usarla siempre que desee empaquetar una extensión para la implementación de VSIX. Sin embargo, si tiene un caso en el que no puede usar la plantilla, puede crear una implementación de VSIX sin usarla.  
  
 Para crear una implementación de VSIX sin usar la plantilla de proyecto de página de inicio, cree primero un archivo. VSIX para la página de inicio de cualquiera de estas dos maneras:  
  
- Agregando los archivos de la página de inicio personalizada a un proyecto VSIX vacío. Para obtener más información, vea [plantilla de Proyecto VSIX](../extensibility/vsix-project-template.md).  
  
- Mediante la creación manual de un archivo. vsix. Para obtener más información, consulte [Cómo: empaquetar manualmente una extensión (implementación VSIX)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
  Para que Visual Studio reconozca una página de inicio, el `Content Element` del manifiesto VSIX debe contener un `CustomExtension Element` que tenga el `Type` atributo establecido en `"StartPage"` . Una extensión de página de inicio que se ha instalado mediante la implementación de VSIX aparece en la lista **Personalizar Página de inicio** de la página Opciones de **Inicio** como *el nombre*de la extensión **[installed Extension]** .  
  
  Si el paquete de la página de inicio incluye ensamblados, debe agregar el registro de la ruta de acceso de enlace para que estén disponibles cuando se inicie Visual Studio. Para ello, asegúrese de que el paquete incluye un archivo. pkgdef con la siguiente información.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Implementación de VSIX para todos los usuarios  
 De forma predeterminada, las extensiones implementadas en los paquetes VSIX solo se instalan para el usuario actual. Puede crear una página de inicio para todos los usuarios del equipo de destino mediante la creación de una implementación para todos los usuarios.  
  
##### <a name="to-create-an-all-users-deployment"></a>Para crear una implementación para todos los usuarios  
  
1. Abra el archivo Extension. vsixmanifest en la vista de código.  
  
2. En el `Identifier` elemento del manifiesto VSIX, agregue un `AllUsers` elemento que tenga un valor de `true` .  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Esto hace que el instalador de VSIX solicite permisos de administrador y, a continuación, instale los archivos en \Common7\IDE\Extensions.  
  
3. Abra el archivo. pkgdef.  
  
4. Modifique el archivo. pkgdef para establecer la página de inicio predeterminada en HKLM agregando lo siguiente, donde *MyStartPage. Xaml* es el nombre del archivo. XAML que contiene la página de inicio.  
  
     [$RootKey $ \StartPage\Default]  
  
     "URI" = "$PackageFolder $ \\ *MyStartPage. Xaml*"  
  
     Esto indica a visual que debe buscar en la nueva ubicación de la página de inicio.  
  
## <a name="file-copy-deployment"></a>Implementación de copia de archivos  
 No es necesario crear un archivo. VSIX para implementar una página de inicio personalizada. En su lugar, puede copiar el marcado y los archivos auxiliares directamente en la carpeta \StartPages\ del usuario. La lista **Personalizar Página de inicio** de la página Opciones de **Inicio** muestra todos los archivos. XAML de esa carpeta, junto con la ruta de acceso; por ejemplo,%UserProfile%\My Documentos\visual Studio *versión*\StartPages \\ *archivo*. Xaml. Si la página de inicio incluye referencias a ensamblados privados, debe copiarlos y pegarlos en la carpeta \Privateassemblies\.  
  
 Para distribuir una página de inicio creada sin empaquetarla en un archivo. vsix, se recomienda usar una estrategia de copia de archivos básica, por ejemplo, un script de batch o cualquier otra tecnología de implementación que le permita colocar los archivos en los directorios necesarios.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Para instalar manualmente una página de inicio personalizada  
  
1. Copie el archivo. XAML que contiene el marcado de la página de inicio, junto con los archivos auxiliares distintos de los ensamblados, y péguelos en la carpeta \StartPages\ del usuario.  
  
2. Si la página de inicio requiere ensamblados, cópielos y péguelos en. \\ *Carpeta de instalación de Visual Studio*\Common7\IDE\PrivateAssemblies \\ .  
  
3. En la lista **Personalizar Página de inicio** de la página Opciones de **Inicio** , seleccione la nueva página de inicio. Para obtener más información, consulte [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Consulte también  
 [Personalización de la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Adición de control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)
