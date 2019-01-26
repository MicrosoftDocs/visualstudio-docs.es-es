---
title: Implementación de las páginas de inicio personalizada | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e89ff96ef73070570b7295ab6256a501d5865b6e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982772"
---
# <a name="deploy-custom-start-pages"></a>Implementar páginas principales personalizadas

Puede implementar páginas principales personalizadas mediante la implementación de VSIX o copiando los archivos en las ubicaciones correctas en el equipo de destino.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Implementación de VSIX con la plantilla de proyecto de página de inicio

Al crear una página de inicio mediante la plantilla de proyecto de la página de inicio y, a continuación, compile el proyecto, Visual Studio crea un *.vsix* archivo que se puede distribuir. Empaquetado de una página de inicio en un *.vsix* archivo le proporciona las siguientes opciones para la implementación, dependiendo de la audiencia prevista:

-   Puede colocar el *.vsix* archivo en un recurso compartido de red o en un sitio Web público. Cuando el archivo se abre la página de inicio se instala automáticamente.

-   Puede cargar el *.vsix* del archivo a la [Galería de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) del sitio Web para que los usuarios pueden instalar mediante el uso de **Administrador de extensiones**.

La plantilla de proyecto de la página de inicio crea una copia de la página de inicio de Visual Studio de forma predeterminada para que pueda modificar la copia y conservar el original.

Puede obtener la plantilla de proyecto de la página de inicio mediante **Administrador de extensiones** o descargándolo desde el sitio Web.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Implementación de VSIX sin usar la plantilla de proyecto de la página de inicio
 Una implementación correcta de VSIX requiere una extensión para instalarse en carpetas que son reconocidas por el proceso de registro VSIX y por **Administrador de extensiones**. Puesto que la plantilla de proyecto de la página de inicio ya especifica las carpetas correctas, se recomienda usar siempre que quiera empaquetar una extensión para la implementación de VSIX. Sin embargo, si tiene un caso en el que no se puede usar la plantilla, puede crear una implementación de VSIX sin usarlo.

 Para crear una implementación de VSIX sin usar la plantilla de proyecto de la página de inicio, cree primero un *.vsix* archivo para la página de inicio de cualquiera de estas dos maneras:

- Mediante la adición de los archivos de la página de inicio personalizados a un proyecto de VSIX vacío. Para obtener más información, consulte [plantilla de proyecto VSIX](../extensibility/vsix-project-template.md).

- Al crear manualmente un *.vsix* archivo. Para crear un *.vsix* archivo manualmente:

  1.  Crear el *extension.vsixmanifest* archivo y la *[Content_Types] .xml* archivo en una carpeta nueva. Para obtener más información, consulte [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md).

  2.  En el Explorador de Windows, haga clic en la carpeta que contiene los dos archivos XML, haga clic en **enviar a**y, a continuación, haga clic en la carpeta comprimida (zip). Cambiar el nombre resultante *.zip* archivo *Filename.vsix*, donde nombreArchivo es el nombre del archivo redistribuible que instala el paquete.

  Para Visual Studio reconocer una página de inicio, la `Content Element` de manifiesto de VSIX debe contener un `CustomExtension Element` que tiene el `Type` atributo establecido en `"StartPage"`. Aparece una extensión de la página de inicio que se ha instalado mediante la implementación de VSIX en el **Personalizar página principal** lista el **inicio** opciones de página como **[instalado la extensión]** *Nombre de la extensión*.

  Si el paquete de la página de inicio incluye los ensamblados, debe agregar el registro de la ruta de acceso de enlace para que estén disponibles cuando se inicia Visual Studio. Para ello, asegúrese de que el paquete incluye un *.pkgdef* archivo que contiene la información siguiente.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Implementación de VSIX para todos los usuarios
 De forma predeterminada, las extensiones implementadas en paquetes VSIX se instalan solo para el usuario actual. Puede realizar una instalación de la página de inicio para todos los usuarios de la máquina de destino mediante la creación de una implementación de todos los usuarios.

### <a name="to-create-an-all-users-deployment"></a>Para crear una implementación de todos los usuarios

1.  Abra el *extension.vsixmanifest* archivo en la vista código.

2.  En el `Identifier` elemento del manifiesto de vsix, agregue un `AllUsers` elemento que tiene un valor de `true`.

    ```
    <AllUsers>true</AllUsers>
    ```

     Esto hace que el instalador de vsix solicitar permisos de administrador y, a continuación, instalar los archivos a *\Common7\IDE\Extensions*.

3.  Abra el *.pkgdef* archivo.

4.  Modificar el *.pkgdef* para establecer la página de inicio predeterminado en HKLM agregando lo siguiente, donde *MyStartPage.xaml* es el nombre de la *.xaml* archivo que contiene el inicio Página.

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     Esto indica a Visual Studio para buscar en la nueva ubicación de la página de inicio.

## <a name="file-copy-deployment"></a>Implementación de copia de archivos
 No es necesario que crear un *.vsix* archivo para implementar una página de inicio personalizada. En su lugar, puede copiar los archivos auxiliares directamente en el usuario y el marcado <em>\StartPages\* carpeta. El **Personalizar página principal</em>*  lista el **inicio** listas de página de opciones de cada *.xaml* en esa carpeta, junto con la ruta de acceso — por ejemplo, *%USERPROFILE%\My Documents\Visual Studio {versión} \StartPages\\{File Name} .xaml*. Si la página de inicio incluye referencias a ensamblados privados, debe copiarlos y pegarlos en el * \PrivateAssemblies\* carpeta.

 Para distribuir una página de inicio que se crea sin empaquetarla en un *.vsix* archivo, se recomienda usar una estrategia de copia de archivo básico, por ejemplo, un script por lotes, o cualquier otra tecnología de implementación que le permite coloca los archivos el directorios requeridos.

### <a name="to-manually-install-a-custom-start-page"></a>Para instalar manualmente una página de inicio personalizada

1.  Copia el *.xaml* archivo que contiene el marcado de página de inicio, junto con todos los archivos auxiliares que no sean ensamblados y péguelos en el usuario * \StartPages\* carpeta.

2.  Si la página de inicio requiere ensamblados, cópielos y péguelos en *... \\{Carpeta de instalación de visual Studio} \Common7\IDE\PrivateAssemblies\\*.

3.  En el **Personalizar página principal** lista el **inicio** opciones, seleccione la nueva página de inicio. Para obtener más información, consulte [personalizar la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Vea también

- [Personalización de la página de inicio](../ide/customizing-the-start-page-for-visual-studio.md)
- [Agregar control de usuario a la página de inicio](../extensibility/adding-user-control-to-the-start-page.md)