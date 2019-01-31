---
title: Procedimiento Crear asociaciones de archivo para una aplicación ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f311705a6cb898ee9bff81a3bbad3890aea92c7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947314"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Procedimiento Creación de asociaciones de archivo para una aplicación ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones pueden asociarse con una o varias extensiones de nombre de archivo, por lo que la aplicación se iniciará automáticamente cuando el usuario abre un archivo de esos tipos. Agregar compatibilidad con extensión de nombre de archivo a un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación es sencilla.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Para crear asociaciones de archivo para una aplicación ClickOnce  
  
1. Crear un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación normalmente, o usar el existente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación.  
  
2. Abra el manifiesto de aplicación con un texto o editor XML, como el Bloc de notas.  
  
3. Busque el elemento `assembly` . Para más información, consulte [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4. Como elemento secundario de la `assembly` elemento, agregue un `fileAssociation` elemento. El `fileAssociation` elemento tiene cuatro atributos:  
  
   - `extension`: La extensión de nombre de archivo que desea asociar a la aplicación.  
  
   - `description`: Una descripción del tipo de archivo, que aparecerá en el shell de Windows.  
  
   - `progid`: Una cadena que identifica el tipo de archivo, para marcarlo en el registro.  
  
   - `defaultIcon`: Un icono que se utilizará para este tipo de archivo. El icono debe agregarse como un recurso de archivo en el manifiesto de aplicación. Para obtener más información, vea [Cómo: Inclusión de un archivo de datos en una aplicación ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Para obtener un ejemplo de la `file` y `fileAssociation` elementos, vea [ \<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Si desea asociar más de un tipo de archivo a la aplicación, agregue más `fileAssociation` elementos. Tenga en cuenta que el `progid` atributo debe ser diferente para cada uno.  
  
6. Cuando haya terminado con el manifiesto de aplicación, vuelva a firmar el manifiesto. Puede hacerlo desde la línea de comandos mediante el uso de *Mage.exe*.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Para más información, vea [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
## <a name="see-also"></a>Vea también  
 [\<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)