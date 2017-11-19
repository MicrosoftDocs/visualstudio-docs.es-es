---
title: "Implementar páginas de inicio personalizada | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2217b77116ea561c32e96fcb7b92b520e680025
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="deploying-custom-start-pages"></a>Implementar páginas de inicio personalizada
Puede implementar las páginas de inicio personalizada mediante la implementación de VSIX o copiando los archivos en las ubicaciones correctas en el equipo de destino.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Implementación de VSIX mediante la plantilla de proyecto de página de inicio  
 Cuando se crea una página de inicio mediante la plantilla de proyecto de la página de inicio y, a continuación, compile el proyecto, Visual Studio crea un archivo .vsix que puede distribuir. Empaquetar una página de inicio en un archivo .vsix le ofrece las siguientes opciones para la implementación, dependiendo de la audiencia de destino:  
  
-   Puede colocar el archivo .vsix en un recurso compartido de red o en un sitio Web público. Cuando un usuario abre el archivo, se instala automáticamente la página de inicio.  
  
-   Puede cargar el archivo .vsix en el [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) sitio Web para que los usuarios pueden instalar mediante el uso de **Extension Manager**.  
  
 La plantilla de proyecto de la página de inicio crea una copia de la página de inicio de Visual Studio de forma predeterminada para que pueda modificar la copia y conservar el original.  
  
 Puede obtener la plantilla de proyecto de la página de inicio mediante **Extension Manager** o mediante la descarga desde el sitio Web.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Implementación de VSIX sin usar la plantilla de proyecto de la página de inicio  
 Una correcta implementación de VSIX requiere una extensión que se instalen en las carpetas que se reconocen mediante el proceso de registro VSIX y **Extension Manager**. Dado que la plantilla de proyecto de la página de inicio ya especifica las carpetas correctas, se recomienda utilizar siempre que desee para empaquetar una extensión para la implementación de VSIX. Sin embargo, si tiene un caso en el que no se puede usar la plantilla, puede crear una implementación de VSIX sin usarla.  
  
 Para crear una implementación de VSIX sin usar la plantilla de proyecto de la página de inicio, en primer lugar, cree un archivo .vsix para la página de inicio de cualquiera de estas dos maneras:  
  
-   Mediante la adición de los archivos de página de inicio personalizados a un proyecto de VSIX vacío. Para obtener más información, consulte [plantilla de proyecto de VSIX](../extensibility/vsix-project-template.md).  
  
-   Mediante la creación manual de un archivo. vsix. Para crear un archivo .vsix manualmente:  
    
    1.  Cree el archivo extension.vsixmanifest y el archivo [Content_Types] .xml en una nueva carpeta. Para obtener más información, consulte [Anatomía de un paquete VSIX](/visualstudio/extensibility/anatomy-of-a-vsix-package).  
  
    2.  En el Explorador de Windows, haga clic en la carpeta que contiene los dos archivos XML, haga clic en Enviar a y, a continuación, haga clic en carpeta comprimida (en zip). Cambie el nombre del archivo .zip resultante a Filename.vsix, donde nombreDeArchivo es el nombre del archivo redistribuible que instala el paquete.  
  
 Para Visual Studio para que reconozca una página de inicio, la `Content Element` de manifiesto de VSIX debe contener una `CustomExtension Element` que tiene el `Type` atributo establecido en `"StartPage"`. Aparece una extensión de la página de inicio que se ha instalado mediante la implementación de VSIX en la **Personalizar página principal** lista el **inicio** opciones de página como **[instalado extensión]** *Nombre de la extensión*.  
  
 Si el paquete de la página de inicio incluye ensamblados, debe agregar el registro de la ruta de acceso de enlace para que estén disponibles cuando se inicia Visual Studio. Para ello, asegúrese de que el paquete incluye un archivo .pkgdef que tiene la siguiente información.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>Implementación de VSIX para todos los usuarios  
 De forma predeterminada, las extensiones se implementan en paquetes VSIX instalan solo para el usuario actual. Puede realizar una instalación de la página de inicio para todos los usuarios de la máquina de destino mediante la creación de una implementación de todos los usuarios.  
  
##### <a name="to-create-an-all-users-deployment"></a>Para crear una implementación de todos los usuarios  
  
1.  Abra el archivo extension.vsixmanifest en la vista código.  
  
2.  En el `Identifier` elemento del manifiesto vsix, agregue un `AllUsers` elemento que tiene un valor de `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Esto hace que el instalador vsix solicitar permisos de administrador y, a continuación, instalar los archivos en \Common7\IDE\Extensions.  
  
3.  Abra el archivo .pkgdef.  
  
4.  Modificar el .pkgdef para establecer la página de inicio predeterminada en HKLM debe agregar lo siguiente, donde *MyStartPage.xaml* es el nombre del archivo .xaml que contiene la página de inicio.  
  
     [$RootKey$ \StartPage\Default]  
  
     "$ De Uri"="$PackageFolder\\*MyStartPage.xaml*"  
  
     Esto indica a superado Visual para buscar en la nueva ubicación de la página de inicio.  
  
## <a name="file-copy-deployment"></a>Implementación de copia de archivos  
 No es necesario crear un archivo .vsix para implementar una página de inicio personalizada. En su lugar, puede copiar los archivos auxiliares y marcado directamente en la carpeta del usuario \StartPages\. El **Personalizar página principal** lista el **inicio** página de opciones enumera todos los archivos .xaml en esa carpeta, junto con la ruta de acceso, por ejemplo, %USERPROFILE%\My documentos\Visual Studio  *versión*\StartPages\\*nombre de archivo*.xaml. Si la página de inicio incluye referencias a ensamblados privados, debe copiarlas y pegarlas en la carpeta \PrivateAssemblies\.  
  
 Para distribuir una página de inicio que se crea sin empaquetado en un archivo .vsix, recomendamos que use una estrategia de copia de archivo básico, por ejemplo, un script por lotes o cualquier otra tecnología de implementación que le permite coloca los archivos en los directorios necesarios.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Para instalar manualmente una página de inicio personalizada  
  
1.  Copie el archivo .xaml que contiene el marcado de la página de inicio, junto con los archivos auxiliares que no sea de ensamblados y péguelos en la carpeta del usuario \StartPages\.  
  
2.  Si la página de inicio requiere ensamblados, cópielos y péguelos en... \\ *Carpeta de instalación de visual Studio*\Common7\IDE\PrivateAssemblies\\.  
  
3.  En el **Personalizar página principal** lista el **inicio** opciones de página, seleccione la nueva página de inicio. Para obtener más información, consulte [personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Adición de control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)