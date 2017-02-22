---
title: "Implementar p&#225;ginas de inicio personalizado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "página de inicio del paquete"
  - "implementar la página de inicio"
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Implementar p&#225;ginas de inicio personalizado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede implementar las páginas principales personalizadas mediante la implementación de VSIX o copiando los archivos en las ubicaciones correctas en el equipo de destino.  
  
## Implementación de VSIX utilizando la plantilla de proyecto de la página de inicio  
 Al crear una página de inicio mediante la plantilla de proyecto de la página de inicio y, a continuación, compile el proyecto, Visual Studio crea un archivo .vsix que puede distribuir. Empaquetado de una página de inicio en un archivo .vsix le ofrece las siguientes opciones para la implementación, dependiendo de la audiencia de destino:  
  
-   Puede colocar el archivo .vsix en un recurso compartido de red o en un sitio Web público. Cuando el archivo se abre la página de inicio se instala automáticamente.  
  
-   Puede cargar el archivo .vsix en el [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) del sitio Web para que los usuarios pueden instalar usando **Administrador de extensiones de**.  
  
 La plantilla de proyecto de la página de inicio crea una copia de la página de inicio de Visual Studio de forma predeterminada para que pueda modificar la copia y conservar el original.  
  
 Puede obtener la plantilla de proyecto de la página de inicio mediante **Administrador de extensiones** o mediante la descarga desde el sitio Web.  
  
## Implementación de VSIX sin usar la plantilla de proyecto de la página de inicio  
 Una correcta implementación de VSIX requiere una extensión que se instalen en carpetas que se reconocen mediante el proceso de registro VSIX y **Administrador de extensiones de**. Dado que la plantilla de proyecto de la página de inicio ya especifica las carpetas correctas, se recomienda utilizar siempre que desee para empaquetar una extensión para la implementación de VSIX. Sin embargo, si tiene un caso en el que se puede utilizar la plantilla, puede crear una implementación de VSIX sin usarla.  
  
 Para crear una implementación de VSIX sin usar la plantilla de proyecto de la página de inicio, primero debe crear un archivo .vsix de la página de inicio de cualquiera de estas dos maneras:  
  
-   Al agregar los archivos de página de inicio personalizados a un proyecto VSIX vacío. Para obtener más información, consulta [Plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).  
  
-   Crear manualmente un archivo .vsix. Para obtener más información, consulta [Procedimiento: empaquetar manualmente una extensión \(implementación VSIX\)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
 Para Visual Studio reconocer una página de inicio, la `Content Element` de manifiesto de VSIX debe contener una `CustomExtension Element` que tiene el `Type` atributo establecido en `"StartPage"`. Aparece una extensión de la página de inicio que se ha instalado mediante la implementación de VSIX en la **Personalizar página principal** lista el **Inicio** opciones de página como **\[extensión instalado\]** *nombre de extensión*.  
  
 Si el paquete de la página de inicio incluye ensamblados, debe agregar el registro de la ruta de acceso de enlace para que estén disponibles cuando se inicia Visual Studio. Para ello, asegúrese de que el paquete incluye un archivo .pkgdef que tiene la información siguiente.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### Implementación de VSIX para todos los usuarios  
 De forma predeterminada, las extensiones implementadas en paquetes VSIX instalan sólo para el usuario actual. Puede realizar una instalación de la página de inicio para todos los usuarios del equipo de destino mediante la creación de una implementación de todos los usuarios.  
  
##### Para crear una implementación de todos los usuarios  
  
1.  En la vista código, abra el archivo extension.vsixmanifest.  
  
2.  En el `Identifier` elemento del manifiesto de vsix, agregue un `AllUsers` elemento que tiene un valor de `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     Esto hace que el instalador de vsix para solicitar permisos de administrador y, a continuación, instalar los archivos en \\Common7\\IDE\\Extensions.  
  
3.  Abra el archivo .pkgdef.  
  
4.  Modificar el .pkgdef para establecer la página de inicio predeterminada en HKLM agregando lo siguiente, donde *MyStartPage.xaml* es el nombre del archivo .xaml que contiene la página de inicio.  
  
     \[$RootKey$ \\StartPage\\Default\]  
  
     "$$PackageFolder"\="de Uri \\*MyStartPage.xaml*"  
  
     Esto indica a Visual soportado para buscar en la nueva ubicación de la página de inicio.  
  
## Implementación de copia de archivos  
 No es necesario crear un archivo .vsix para implementar una página principal personalizada. En su lugar, puede copiar los archivos auxiliares y marcado directamente en la carpeta del usuario \\StartPages\\. El **Personalizar página principal** lista el **Inicio** página de opciones muestran todos los archivos .xaml en esa carpeta, junto con la ruta de acceso, por ejemplo, %USERPROFILE%\\My Documents\\Visual Studio *versión*\\StartPages\\*nombre de archivo*.xaml. Si la página de inicio incluye referencias a ensamblados privados, debe copiarlos y pegarlos en la carpeta \\PrivateAssemblies\\.  
  
 Para distribuir una página de inicio que se crea sin empaquetado en un archivo .vsix, se recomienda usar una estrategia de copia de archivo básico, por ejemplo, un script por lotes, o cualquier otra tecnología de implementación que le permite coloca los archivos en los directorios necesarios.  
  
#### Para instalar manualmente una página principal personalizada  
  
1.  Copie el archivo .xaml que contiene el marcado de la página de inicio, junto con los archivos auxiliares distintos ensamblados y péguelos en la carpeta del usuario \\StartPages\\.  
  
2.  Si la página de inicio requiere ensamblados, cópielos y péguelos en... \\*Carpeta de instalación de visual Studio*\\Common7\\IDE\\PrivateAssemblies\\.  
  
3.  En el **Personalizar página principal** lista el **Inicio** opciones de página, seleccione la nueva página de inicio. Para obtener más información, consulta [Personalizar la página principal](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## Vea también  
 [Personalizar la página principal](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Agregar Control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)