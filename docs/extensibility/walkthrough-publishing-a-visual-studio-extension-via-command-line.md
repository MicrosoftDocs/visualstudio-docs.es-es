---
title: 'Tutorial: Publicar una extensión de Visual Studio a través de la línea de comandos | Microsoft Docs'
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb35365220ade512defc180b06e46b95999dfa7b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857220"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Tutorial: Publicación de una extensión de Visual Studio a través de la línea de comandos

En este tutorial se muestra cómo publicar una extensión de Visual Studio en Visual Studio Marketplace mediante la línea de comandos. Cuando se agrega la extensión en Marketplace, los desarrolladores pueden usar el [ **extensiones y actualizaciones** ](../ide/finding-and-using-visual-studio-extensions.md) cuadro de diálogo para buscar allí extensiones nuevas y actualizadas.

VsixPublisher.exe es la herramienta de línea de comandos para la publicación de extensiones de Visual Studio Marketplace. Se puede acceder desde ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Los comandos disponibles en esta herramienta son: **publicar**, **CreatePublisher para**, **deletePublisher**, **deleteExtension**,  **inicio de sesión**, **logout**.

## <a name="commands"></a>Comandos

### <a name="publish"></a>publicar

Publica una extensión en Marketplace. La extensión puede ser un archivo vsix, un archivo exe o msi o un vínculo. Si la extensión ya existe con la misma versión, sobrescribirá la extensión. Si la extensión no existe, creará una nueva extensión.

|Opciones de comando |Descripción |
|---------|---------|
|carga (obligatorio) | Ser una ruta de acceso a la carga para publicar o un vínculo que se usará como la "URL de información adicional". |
|publishManifest (obligatorio) | Ruta de acceso a la publicación del manifiesto archivo que se usará. |
|ignoreWarnings | Lista de advertencias para pasar por alto al publicar una extensión. Estas advertencias se muestran como mensajes de la línea de comandos al publicar una extensión. (por ejemplo, "VSIXValidatorWarning01, VSIXValidatorWarning02")  
|personalAccessToken | Personal Access Token (PAT) que se usa para autenticar el publicador. Si no se proporciona, se adquiere el PAT de los usuarios que ha iniciado sesión. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>CreatePublisher para

Crea un publicador en Marketplace. También registra el publicador en la máquina para las futuras acciones (por ejemplo, una extensión de eliminación y publicación).

|Opciones de comando |Descripción |
|---------|---------|
|displayName (obligatorio) | Nombre para mostrar del publicador. |
|publisherName (obligatorio) | El nombre del publicador (por ejemplo, el identificador). |
|personalAccessToken (obligatorio) | Token de acceso personal que se usa para autenticar el publicador. |
|shortDescription | Una descripción breve del publicador (no es un archivo). |
|longDescription | Una descripción larga del publicador (no es un archivo). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Elimina un publicador en Marketplace.

|Opciones de comando |Descripción |
|---------|---------|
|publisherName (obligatorio) | El nombre del publicador (por ejemplo, el identificador). |
|personalAccessToken (obligatorio) | Token de acceso personal que se usa para autenticar el publicador. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Elimina una extensión de Marketplace.

|Opciones de comando |Descripción |
|---------|---------|
|extensionName (obligatorio) | El nombre de la extensión que se va a eliminar. |
|publisherName (obligatorio) | El nombre del publicador (por ejemplo, el identificador). |
|personalAccessToken | Token de acceso personal que se usa para autenticar el publicador. Si no se proporciona, se adquiere el pat de los usuarios que ha iniciado sesión. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>inicio de sesión

Registra un publicador en el equipo.

|Opciones de comando |Descripción |
|---------|---------|
|personalAccessToken (obligatorio | Token de acceso personal que se usa para autenticar el publicador. |
|publisherName (obligatorio) | El nombre del publicador (por ejemplo, el identificador). |
|Sobrescribir | Especifica que se debe sobrescribir cualquier publicador existente con el nuevo token de acceso personal. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>Cierre de sesión

Registra un publicador de la máquina.

|Opciones de comando |Descripción |
|---------|---------|
|publisherName (obligatorio) | El nombre del publicador (por ejemplo, el identificador). |
|ignoreMissingPublisher | Especifica que la herramienta debe no de error si el publicador especificado no es ya ha iniciado sesión. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>archivo publishManifest

Usa un archivo publishManifest el **publicar** comando. Representa todos los metadatos acerca de la extensión que necesita saber el Marketplace. Si la extensión que se están cargando procede de una extensión VSIX, la propiedad "identity" solo debe tener el "internalName" establecida. Esto es porque el resto de las propiedades "identity" se puede generar desde el archivo vsixmanifest. Si la extensión es un archivo msi y exe o una extensión de vínculo, el usuario debe proporcionar los campos obligatorios en la propiedad "identity". El resto del manifiesto contiene información específica de Marketplace (por ejemplo, categorías, si preguntas y respuestas está habilitada, etcetera.).

Ejemplo de archivo de publishManifest de extensión VSIX:

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

Ejemplo de archivo publishManifest MSI y EXE o vínculo:

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

Archivos de recursos se pueden proporcionar para la incrustación de cosas como las imágenes en el archivo Léame. Por ejemplo, si una extensión tiene el documento de marcado siguiente "Introducción":

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Con el fin de resolver "images/testlogo.png" en el ejemplo anterior, un usuario puede proporcionar "assetFiles" en su publicación manifiesto como a continuación:

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

### <a name="prerequisites"></a>Requisitos previos

Para seguir este tutorial, debe instalar el SDK de Visual Studio. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio

En este caso, usamos una extensión predeterminada de VSPackage, pero los mismos pasos son válidos para cada tipo de extensión.

1. Cree un VSPackage en C# denominado "TestPublish" que tiene un comando de menú. Para obtener más información, consulte [crear su primera extensión: Hola mundo](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Empaquetar la extensión

1. Actualizar extensión vsixmanifest con la información sobre el nombre de producto, el autor y la versión correcta.

   ![actualizar extensión vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilar la extensión **versión** modo. Ahora la extensión se empaquetan como un archivo VSIX en la carpeta \bin\Release.

3. Hacer doble clic en el archivo VSIX para comprobar la instalación.

### <a name="test-the-extension"></a>Probar la extensión

 Antes de distribuir la extensión, compilar y probarlo para asegurarse de que está instalado correctamente en la instancia experimental de Visual Studio.

1. En Visual Studio, inicie la depuración. Para abrir una instancia experimental de Visual Studio.

2. En la instancia experimental, vaya a la **herramientas** menú y haga clic en **extensiones y actualizaciones...** . La extensión TestPublish debe aparecer en el panel central y habilitarse.

3. En el **herramientas** menú, asegúrese de que ve el comando de prueba.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publicar la extensión en Marketplace a través de la línea de comandos

1. Asegúrese de que ha creado la versión de lanzamiento de la extensión y que está actualizada.

2. Asegúrese de que ha creado archivos publishmanifest.json y overview.md.

3. Abra la línea de comandos y navegue al directorio de ${VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\.

4. Para crear un nuevo publicador, use el siguiente comando:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Creación correcta del publicador, verá el siguiente mensaje de la línea de comandos:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Puede comprobar el nuevo publicador que creó, vaya a [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Para publicar una nueva extensión, use el siguiente comando:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Creación correcta del publicador, verá el siguiente mensaje de la línea de comandos:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Puede comprobar la nueva extensión publicó yendo a [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instalar la extensión de Visual Studio Marketplace

Ahora que se ha publicado la extensión, instalarlo en Visual Studio y pruébela.

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones...** .

2. Haga clic en **Online** y, a continuación, busque TestPublish.

3. Haga clic en **Descargar**. A continuación, se programará la extensión para la instalación.

4. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Quitar la extensión

Puede quitar la extensión de Visual Studio Marketplace y de su equipo.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Para quitar la extensión de Marketplace a través de la línea de comandos

1. Si desea quitar una extensión, use el siguiente comando:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. La eliminación de la extensión se realiza correctamente, verá el siguiente mensaje de la línea de comandos:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Para quitar la extensión de su equipo

1. En Visual Studio, en el **herramientas** menú, haga clic en **extensiones y actualizaciones...** .

2. Seleccione "MyVsixExtension" y, a continuación, haga clic en **desinstalar**. A continuación, se programará la extensión para la desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
