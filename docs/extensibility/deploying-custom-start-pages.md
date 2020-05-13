---
title: Implementación de páginas de inicio personalizadas ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712227"
---
# <a name="deploy-custom-start-pages"></a>Implementar páginas de inicio personalizadas

Puede implementar páginas de inicio personalizadas mediante la implementación de VSIX o copiando los archivos en las ubicaciones correctas en el equipo de destino.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Implementación de VSIX mediante la plantilla de proyecto Página de inicio

Al crear una página de inicio mediante la plantilla de proyecto de página de inicio y, a continuación, compilar el proyecto, Visual Studio crea un archivo *.vsix* que puede distribuir. Empaquetar una página de inicio en un archivo *.vsix* le ofrece las siguientes opciones de implementación, en función de la audiencia prevista:

- Puede colocar el archivo *.vsix* en un recurso compartido de red o en un sitio Web público. Cuando alguien abre el archivo, la página de inicio se instala automáticamente.

- Puede cargar el archivo *.vsix* en el sitio Web de [Visual Studio Marketplace](https://marketplace.visualstudio.com/) para que los usuarios puedan instalarlo mediante Extension **Manager**.

La plantilla de proyecto Página de inicio crea una copia de la página de inicio de Visual Studio predeterminada para que pueda modificar la copia y conservar el original.

Puede obtener la plantilla de proyecto de página de inicio mediante **el Administrador de extensiones** o descargándola desde el sitio Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Implementación de VSIX sin usar la plantilla de proyecto de página de inicio
 Una implementación correcta de VSIX requiere que se instale una extensión en carpetas reconocidas por el proceso de registro de VSIX y por **Extension Manager**. Dado que la plantilla de proyecto de página de inicio ya especifica las carpetas correctas, se recomienda usarla siempre que desee empaquetar una extensión para la implementación de VSIX. Sin embargo, si tiene un caso en el que no puede usar la plantilla, puede crear una implementación VSIX sin usarla.

 Para crear una implementación VSIX sin usar la plantilla de proyecto Página de inicio, primero cree un archivo *.vsix* para la página de inicio de cualquiera de estas dos maneras:

- Agregando los archivos de la página de inicio personalizada a un proyecto VSIX vacío. Para obtener más información, consulte Plantilla de [proyecto VSIX](../extensibility/vsix-project-template.md).

- Creando manualmente un archivo *.vsix.* Para crear un archivo *.vsix* manualmente:

   1. Cree el archivo *extension.vsixmanifest* y el archivo *[Content_Types].xml* en una carpeta nueva. Para obtener más información, consulte [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. En el Explorador de Windows, haga clic con el botón secundario en la carpeta que contiene los dos archivos XML, haga clic en **Enviar a**y, a continuación, haga clic en Carpeta comprimida (comprimida). Cambie el nombre del archivo *.zip* resultante a *Filename.vsix*, donde Filename es el nombre del archivo redistribuible que instala el paquete.

Para que Visual Studio reconozca `Content Element` una página de inicio, `CustomExtension Element` el `Type` manifiesto de `"StartPage"`VSIX debe contener un que tenga el atributo establecido en . Aparece una extensión de página de inicio que se ha instalado mediante la implementación de VSIX en la lista **Personalizar página** de inicio de la página Opciones de **inicio** como Nombre de *extensión* **[Extensión instalada]** .

Si el paquete de la página de inicio incluye ensamblados, debe agregar el registro de ruta de acceso de enlace para que estén disponibles cuando se inicie Visual Studio. Para ello, asegúrese de que el paquete incluye un archivo *.pkgdef* que tiene la siguiente información.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Implementación de VSIX para todos los usuarios
 De forma predeterminada, las extensiones implementadas en paquetes VSIX solo se instalan para el usuario actual. Puede realizar una instalación de la página de inicio para todos los usuarios del equipo de destino mediante la creación de una implementación de todos los usuarios.

### <a name="to-create-an-all-users-deployment"></a>Para crear una implementación de todos los usuarios

1. Abra el archivo *extension.vsixmanifest* en la vista de código.

2. En `Identifier` el elemento del manifiesto vsix, agregue `AllUsers` un `true`elemento que tenga un valor de .

    ```
    <AllUsers>true</AllUsers>
    ```

     Esto hace que el instalador de vsix solicite permisos de administrador y, a continuación, instale los archivos en *.*

3. Abra el archivo *.pkgdef.*

4. Modifique *el archivo .pkgdef* para establecer la página de inicio predeterminada en HKLM agregando lo siguiente, donde *MyStartPage.xaml* es el nombre del archivo *.xaml* que contiene la página de inicio.

     [$RootKey$-StartPage-Predeterminado]

     "Uri"-"$PackageFolder$\\*MyStartPage.xaml"*

     Esto indica a Visual Studio que busque en la nueva ubicación de la página de inicio.

## <a name="file-copy-deployment"></a>Implementación de copia de archivos
 No es necesario crear un archivo *.vsix* para implementar una página de inicio personalizada. En su lugar, puede copiar el marcado y los archivos <em>auxiliares\* directamente en la carpeta de la página de inicio del usuario. *Customize Start Page</em> La* lista * Personalizar página de inicio de la página Opciones de **inicio** muestra todos los archivos *.xaml* de esa carpeta, junto con la ruta de acceso, por ejemplo, *%USERPROFILE%,Mis documentos, Visual Studio, versión, StartPages,\\Nombre*de archivo y .xaml . Si la página de inicio incluye referencias a ensamblados privados, debe\* copiarlos y pegarlos en la carpeta * .

 Para distribuir una página de inicio que ha creado sin empaquetarla en un archivo *.vsix,* le recomendamos que utilice una estrategia básica de copia de archivos, por ejemplo, un script por lotes o cualquier otra tecnología de implementación que le permita colocar los archivos en los directorios necesarios.

### <a name="to-manually-install-a-custom-start-page"></a>Para instalar manualmente una página de inicio personalizada

1. Copie el archivo *.xaml* que contiene el marcado de la página de inicio, junto con los archivos\* auxiliares que no sean ensamblados, y péguelos en la carpeta *-StartPages del usuario.

2. Si la página de inicio requiere ensamblados, cópielos y péguelos en *.. •Carpeta de instalación de Visual Studio, Common7, IDE, PrivateAssemblies\\. \\*

3. En la lista **Personalizar página** de inicio de la página Opciones de **inicio,** seleccione la nueva página de inicio. Para obtener más información, consulte [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md)
- [Agregar control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)
