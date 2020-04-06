---
title: Publicar extensión mediante la línea de comandos
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697126"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Tutorial: Publicación de una extensión de Visual Studio a través de la línea de comandos

En este tutorial se muestra cómo publicar una extensión de Visual Studio en Visual Studio Marketplace mediante la línea de comandos. Al agregar la extensión a Marketplace, los desarrolladores pueden usar el cuadro de diálogo [**Extensiones y actualizaciones**](../ide/finding-and-using-visual-studio-extensions.md) para buscar extensiones nuevas y actualizadas.

VsixPublisher.exe es la herramienta de línea de comandos para publicar extensiones de Visual Studio en Marketplace. Se puede tener acceso a ella desde $-VSInstallDir-VSSDK-VisualStudioIntegration-Tools-Bin-VsixPublisher.exe. Los comandos disponibles en esta herramienta son: **publish**, **createPublisher**, **deletePublisher**, **deleteExtension**, **login**, **logout**.

## <a name="commands"></a>Comandos

### <a name="publish"></a>Publicar

Publica una extensión en Marketplace. La extensión puede ser un vsix, un archivo exe/msi o un vínculo. Si la extensión ya existe con la misma versión, sobrescribirá la extensión. Si la extensión aún no existe, creará una nueva extensión.

|Opciones de comando |Descripción |
|---------|---------|
|carga útil (obligatorio) | Una ruta de acceso a la carga útil para publicar o un vínculo para usar como la "URL de información más". |
|publishManifest (obligatorio) | Ruta de acceso al archivo de manifiesto de publicación que se va a usar. |
|ignoreWarnings | Lista de advertencias que se deben omitir al publicar una extensión. Estas advertencias se muestran como mensajes de línea de comandos al publicar una extensión. (por ejemplo, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Token de acceso personal (PAT) que se utiliza para autenticar al editor. Si no se proporciona, la PAT se adquiere de los usuarios que han iniciado sesión. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Crea un publicador en Marketplace. También registra el publicador en el equipo para acciones futuras (por ejemplo, eliminar/publicar una extensión).

|Opciones de comando |Descripción |
|---------|---------|
|displayName (obligatorio) | Nombre para mostrar del editor. |
|publisherName (obligatorio) | El nombre del editor (por ejemplo, el identificador). |
|personalAccessToken (obligatorio) | Token de acceso personal que se utiliza para autenticar al editor. |
|shortDescription | Una breve descripción del editor (no un archivo). |
|longDescription | Una descripción larga del editor (no un archivo). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Elimina un editor en Marketplace.

|Opciones de comando |Descripción |
|---------|---------|
|publisherName (obligatorio) | El nombre del editor (por ejemplo, el identificador). |
|personalAccessToken (obligatorio) | Token de acceso personal que se utiliza para autenticar al editor. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Elimina una extensión de Marketplace.

|Opciones de comando |Descripción |
|---------|---------|
|extensionName (obligatorio) | El nombre de la extensión que se desea eliminar. |
|publisherName (obligatorio) | El nombre del editor (por ejemplo, el identificador). |
|personalAccessToken | Token de acceso personal que se utiliza para autenticar al editor. Si no se proporciona, el pat se adquiere de los usuarios que han iniciado sesión. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Registra un publicador en la máquina.

|Opciones de comando |Descripción |
|---------|---------|
|personalAccessToken (requerido | Token de acceso personal que se utiliza para autenticar al editor. |
|publisherName (obligatorio) | El nombre del editor (por ejemplo, el identificador). |
|overwrite | Especifica que cualquier publicador existente debe sobrescribirse con el nuevo token de acceso personal. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Cierra la sesión de un editor de la máquina.

|Opciones de comando |Descripción |
|---------|---------|
|publisherName (obligatorio) | El nombre del editor (por ejemplo, el identificador). |
|ignoreMissingPublisher | Especifica que la herramienta no debe error si el publicador especificado aún no ha iniciado sesión. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest archivo

El comando **publish** utiliza un archivo publishManifest. Representa todos los metadatos sobre la extensión que Marketplace necesita saber. Si la extensión que se carga es desde una extensión VSIX, la propiedad "identity" solo debe tener el conjunto "internalName". Esto se debe a que el resto de las propiedades "identity" se pueden generar a partir del archivo vsixmanifest. Si la extensión es un msi/exe o una extensión de vínculo, el usuario debe proporcionar los campos obligatorios en la propiedad "identity". El resto del manifiesto contiene información específica del Marketplace (por ejemplo, categorías, si Q&A está habilitada, etc.).

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

Ejemplo de archivo publishManifest de MSI/EXE o LINK:

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

## <a name="asset-files"></a>Archivos de activos

Se pueden proporcionar archivos de activos para incrustar cosas como imágenes en el archivo Léame. Por ejemplo, si una extensión tiene el siguiente documento de Markdown de "resumen":

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Para resolver "images/testlogo.png" en el ejemplo anterior, un usuario puede proporcionar "assetFiles" en su manifiesto de publicación como se muestra a continuación:

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

Para seguir este tutorial, debe instalar SDK de Visual Studio. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

### <a name="create-a-visual-studio-extension"></a>Crear una extensión de Visual Studio

En este caso, usaremos una extensión de VSPackage predeterminada, pero los mismos pasos son válidos para cada tipo de extensión.

1. Crear un VSPackage en C- denominado "TestPublish" que tiene un comando de menú. Para obtener más información, consulte [Creación de la primera extensión: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Empaquetado de la extensión

1. Actualice la extensión vsixmanifest con la información correcta sobre el nombre, el autor y la versión del producto.

   ![extensión de actualización vsixmanifest](media/update-extension-vsixmanifest.png)

2. Cree la extensión en el modo **de versión.** Ahora, la extensión se empaquetará como un VSIX en la carpeta .bin.Release.

3. Puede hacer doble clic en VSIX para comprobar la instalación.

### <a name="test-the-extension"></a>Pruebe la extensión

 Antes de distribuir la extensión, compile y pruébela para asegurarse de que está instalada correctamente en la instancia experimental de Visual Studio.

1. En Visual Studio, inicie la depuración. para abrir una instancia experimental de Visual Studio.

2. En la instancia experimental, vaya al menú **Herramientas** y haga clic en **Extensiones y actualizaciones...**. La extensión TestPublish debe aparecer en el panel central y estar habilitada.

3. En el menú **Herramientas,** asegúrese de ver el comando test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publique la extensión en Marketplace a través de la línea de comandos

1. Asegúrese de que ha creado la versión Release de la extensión y de que está actualizada.

2. Asegúrese de que ha creado archivos publishmanifest.json y overview.md.

3. Abra la línea de comandos y desplácese hasta el directorio $-VSInstallDir-VSSDK-VisualStudioIntegration-Tools-Bin.

4. Para crear un nuevo editor, utilice el siguiente comando:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. En la creación correcta del publicador, verá el siguiente mensaje de línea de comandos:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Puede comprobar el nuevo editor que creó navegando a [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Para publicar una nueva extensión, utilice el siguiente comando:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. En la creación correcta del publicador, verá el siguiente mensaje de línea de comandos:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Puede comprobar la nueva extensión que publicó navegando a [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instale la extensión desde Visual Studio Marketplace

Ahora que se ha publicado la extensión, instálela en Visual Studio y pruébela allí.

1. En Visual Studio, en el menú **Herramientas,** haga clic en **Extensiones y actualizaciones...**.

2. Haga clic en **En línea** y, a continuación, busque TestPublish.

3. Haga clic en **Descargar**. La extensión se programará para su instalación.

4. Para completar la instalación, cierre todas las instancias de Visual Studio.

## <a name="remove-the-extension"></a>Eliminación de la extensión

Puede quitar la extensión de Visual Studio Marketplace y del equipo.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Para eliminar la extensión del Marketplace a través de la línea de comandos

1. Si desea eliminar una extensión, utilice el siguiente comando:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. En la eliminación correcta de la extensión, verá el siguiente mensaje de línea de comandos:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Para eliminar la extensión del ordenador

1. En Visual Studio, en el menú **Herramientas** , haga clic en **Extensiones y actualizaciones**.

2. Seleccionar "MyVsixExtension" y luego haga clic **en Desinstalar**. La extensión se programará para su desinstalación.

3. Para completar la desinstalación, cierre todas las instancias de Visual Studio.
