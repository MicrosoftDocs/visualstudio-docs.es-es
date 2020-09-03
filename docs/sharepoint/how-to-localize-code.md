---
title: 'Cómo: localizar código | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c1963ff0b6ef317dfa1a2c8154a1628710dc562
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016694"
---
# <a name="how-to-localize-code"></a>Cómo: localizar código
  El código sin localizar usa valores de cadena codificados de forma rígida. Para localizar cadenas de código, sustitúyalas por llamadas a <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, que es un método que hace referencia a los recursos localizados.

## <a name="localize-code"></a>Localizar código

#### <a name="to-localize-code"></a>Para localizar el código

1. En **Explorador de soluciones**, abra el menú contextual de un elemento de proyecto y, a continuación, elija **Agregar**  >  **módulo**.

     Elija la plantilla de **archivo de recursos** .

    > [!NOTE]
    > Asegúrese de agregar el archivo de recursos a un elemento de proyecto de SharePoint para que esté disponible la propiedad Tipo de implementación. Esta propiedad es necesaria más adelante en este procedimiento.

2. Asigne al archivo de recursos de idioma predeterminado el nombre que prefiera anexado con una extensión *. resx* , como *MyAppResources. resx*.

3. Repita los pasos 1 y 2 para agregar archivos de recursos independientes al elemento de proyecto de SharePoint: uno para cada idioma localizado.

     Use el mismo nombre base para cada archivo de recursos localizado, pero agregue el identificador de la referencia cultural. Por ejemplo, asigne un nombre a un recurso localizado en Alemán *MyAppResources.de-de. resx*.

4. Abra cada uno de los archivos de recursos y agregue las cadenas localizadas. Use los mismos identificadores de cadena en cada archivo.

5. Cambie el valor de la propiedad **tipo de implementación** de cada archivo de recursos a **AppGlobalResource** para que cada archivo se implemente en la carpeta App_GlobalResources del servidor.

6. Deje el valor de la propiedad **acción de compilación** de cada archivo como **recurso incrustado**.

     Los recursos incrustados se compilan en el archivo DLL del proyecto.

7. Compile el proyecto para crear los archivos DLL satélite de recursos.

8. En el **Diseñador de paquetes**, elija la pestaña **Opciones avanzadas** y, a continuación, agregue el ensamblado satélite.

9. En el cuadro **Ubicación** , anteponga una carpeta de ID. de referencia cultural a la ruta de acceso de ubicación, por ejemplo, *de-de \\ \<Project Item Name>.resources.dll*.

10. Si la solución aún no hace referencia el ensamblado System.Web, agregue una referencia y una directiva del código al espacio de nombres <xref:System.Web>.

11. Busque todas las cadenas codificadas de forma rígida en el código visibles para los usuarios, como texto de la interfaz de usuario, errores y texto del mensaje. Reemplácelas por una llamada al método <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> utilizando la sintaxis siguiente:

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Elija la tecla **F5** para compilar y ejecutar la aplicación.

13. En SharePoint, cambie el idioma de presentación predeterminado.

     Las cadenas localizadas aparecen en la aplicación. Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.

## <a name="see-also"></a>Consulte también
- [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Cómo: localizar una característica](../sharepoint/how-to-localize-a-feature.md)
- [Cómo: localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Cómo: agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)
