---
title: Publicar extensión mediante la línea de comandos
description: Obtenga información sobre cómo usar la línea de comandos para publicar una extensión en el Visual Studio Marketplace, lo que permite a los desarrolladores buscar extensiones nuevas y actualizadas.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4132d878ff1ec7689be890446a1849577fafd30
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877928"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Tutorial: publicar una extensión de Visual Studio mediante la línea de comandos

En este tutorial se muestra cómo publicar una extensión de Visual Studio en el Visual Studio Marketplace mediante la línea de comandos. Al agregar la extensión a Marketplace, los desarrolladores pueden usar el cuadro de diálogo [**extensiones y actualizaciones**](../ide/finding-and-using-visual-studio-extensions.md) para buscar extensiones nuevas y actualizadas.

VsixPublisher.exe es la herramienta de línea de comandos para publicar extensiones de Visual Studio en Marketplace. Se puede tener acceso a ella desde $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Los comandos disponibles en esta herramienta son: **Publish**, **createPublisher**, **deletePublisher**, **deleteExtension**, **login**, **Logout**.

## <a name="commands"></a>Comandos

### <a name="publish"></a>Publicar

Publica una extensión en Marketplace. La extensión puede ser VSIX, un archivo exe o MSI, o un vínculo. Si la extensión ya existe con la misma versión, sobrescribirá la extensión. Si la extensión no existe, se creará una nueva extensión.

|Opciones de comando |Description |
|---------|---------|
|carga útil (obligatorio) | Una ruta de acceso a la carga que se va a publicar o un vínculo que se usará como "más información URL". |
|publishManifest (obligatorio) | Ruta de acceso al archivo de manifiesto de publicación que se va a usar. |
|ignoreWarnings | Lista de advertencias que se van a omitir al publicar una extensión. Estas advertencias se muestran como mensajes de línea de comandos al publicar una extensión. (por ejemplo, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Token de acceso personal (PAT) que se usa para autenticar el publicador. Si no se proporciona, PAT se adquiere de los usuarios que han iniciado sesión. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Crea un publicador en Marketplace. También registra el publicador en el equipo para las siguientes acciones (por ejemplo, eliminar o publicar una extensión).

|Opciones de comando |Description |
|---------|---------|
|displayName (obligatorio) | Nombre para mostrar del publicador. |
|publisherName (obligatorio) | Nombre del publicador (por ejemplo, el identificador). |
|personalAccessToken (obligatorio) | Token de acceso personal que se usa para autenticar el publicador. |
|shortDescription | Breve descripción del publicador (no un archivo). |
|longDescription | Una descripción larga del publicador (no un archivo). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Elimina un publicador en Marketplace.

|Opciones de comando |Description |
|---------|---------|
|publisherName (obligatorio) | Nombre del publicador (por ejemplo, el identificador). |
|personalAccessToken (obligatorio) | Token de acceso personal que se usa para autenticar el publicador. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Elimina una extensión de Marketplace.

|Opciones de comando |Description |
|---------|---------|
|extensionName (obligatorio) | Nombre de la extensión que se va a eliminar. |
|publisherName (obligatorio) | Nombre del publicador (por ejemplo, el identificador). |
|personalAccessToken | Token de acceso personal que se usa para autenticar el publicador. Si no se proporciona, Pat se adquiere de los usuarios que han iniciado sesión. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Registra un publicador en la máquina.

|Opciones de comando |Description |
|---------|---------|
|personalAccessToken (obligatorio | Token de acceso personal que se usa para autenticar el publicador. |
|publisherName (obligatorio) | Nombre del publicador (por ejemplo, el identificador). |
|overwrite | Especifica que cualquier publicador existente debe sobrescribirse con el nuevo token de acceso personal. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Registra un publicador fuera de la máquina.

|Opciones de comando |Description |
|---------|---------|
|publisherName (obligatorio) | Nombre del publicador (por ejemplo, el identificador). |
|ignoreMissingPublisher | Especifica que la herramienta no debe ser un error si el publicador especificado todavía no tiene una sesión iniciada. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>archivo publishManifest

El comando **Publish** usa un archivo publishManifest. Representa todos los metadatos acerca de la extensión que debe conocer el Marketplace. Si la extensión que se va a cargar es de una extensión VSIX, la propiedad "Identity" solo debe tener establecido el valor "internalName". Esto se debe a que el resto de las propiedades de "Identity" pueden generarse a partir del archivo vsixmanifest. Si la extensión es MSI/exe o una extensión de vínculo, el usuario debe proporcionar los campos obligatorios en la propiedad "Identity". El resto del manifiesto contiene información específica del Marketplace (por ejemplo, categorías, si Q&A está habilitado, etc.).

Ejemplo de archivo publishManifest de extensión VSIX:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

Ejemplo de archivo MSI/EXE o LINK publishManifest:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Archivos de recursos

Se pueden proporcionar archivos de recursos para insertar elementos como imágenes en el archivo Léame. Por ejemplo, si una extensión tiene el siguiente documento de Markdown "información general":

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Con el fin de resolver "images/testlogo.png" en el ejemplo anterior, un usuario puede proporcionar "assetFiles" en el manifiesto de publicación, como se muestra a continuación:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Tutorial de publicación

### <a name="prerequisites"></a>Prerrequisitos

Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio

En este caso, usaremos una extensión VSPackage predeterminada, pero los mismos pasos son válidos para cada tipo de extensión.

1. Cree un VSPackage en C# denominado "TestPublish" que tenga un comando de menú. Para obtener más información, consulte [crear la primera extensión: Hola mundo](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Empaquetado de la extensión

1. Actualice la extensión vsixmanifest con la información correcta sobre el nombre del producto, el autor y la versión.

   ![actualizar vsixmanifest de extensión](media/update-extension-vsixmanifest.png)

2. Compilar la extensión en modo de **versión** . Ahora la extensión se empaquetará como VSIX en la carpeta \bin\Release

3. Puede hacer doble clic en VSIX para comprobar la instalación.

### <a name="test-the-extension"></a>Prueba de la extensión

 Antes de distribuir la extensión, compilarla y probarla para asegurarse de que se ha instalado correctamente en la instancia experimental de Visual Studio.

1. En Visual Studio, inicie la depuración. para abrir una instancia experimental de Visual Studio.

2. En la instancia experimental, vaya al menú **herramientas** y haga clic en **extensiones y actualizaciones..**.. La extensión TestPublish debe aparecer en el panel central y estar habilitada.

3. En el menú **herramientas** , asegúrese de que ve el comando prueba.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publicación de la extensión en Marketplace mediante la línea de comandos

1. Asegúrese de que ha creado la versión de lanzamiento de la extensión y de que está actualizada.

2. Asegúrese de haber creado publishmanifest.jsarchivos en y overview.md.

3. Abra la línea de comandos y navegue hasta el directorio $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\

4. Para crear un nuevo publicador, use el siguiente comando:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Al crear el publicador correctamente, verá el siguiente mensaje de línea de comandos:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Puede comprobar el nuevo publicador que ha creado desplazándose a [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Para publicar una nueva extensión, use el siguiente comando:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Al crear el publicador correctamente, verá el siguiente mensaje de línea de comandos:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Puede comprobar la nueva extensión publicada desplazándose a [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instale la extensión desde el Visual Studio Marketplace

Ahora que se ha publicado la extensión, instálela en Visual Studio y pruébelo en ella.

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones..**..

2. Haga clic en **en línea** y busque TestPublish.

3. Haga clic en **Descargar**. La extensión se programará para su instalación.

4. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Eliminación de la extensión

Puede quitar la extensión del Visual Studio Marketplace y del equipo.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Para quitar la extensión de Marketplace a través de la línea de comandos

1. Si desea quitar una extensión, use el siguiente comando:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Al eliminar la extensión correctamente, verá el siguiente mensaje de línea de comandos:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Para quitar la extensión del equipo

1. En Visual Studio, en el menú **herramientas** , haga clic en **extensiones y actualizaciones**.

2. Seleccione "MyVsixExtension" y, a continuación, haga clic en **desinstalar**. La extensión se programará para la desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
