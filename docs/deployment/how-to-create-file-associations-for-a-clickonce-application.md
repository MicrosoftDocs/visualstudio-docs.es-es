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
ms.openlocfilehash: 0526351d2b3e2c223aacbe0e58d9ee39bd1b19c4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68924555"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Procedimiento Creación de asociaciones de archivo para una aplicación ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]las aplicaciones pueden estar asociadas a una o varias extensiones de nombre de archivo, de modo que la aplicación se iniciará automáticamente cuando el usuario abra un archivo de esos tipos. Agregar compatibilidad con la extensión de nombre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] de archivo a una aplicación es sencillo.

### <a name="to-create-file-associations-for-a-clickonce-application"></a>Para crear asociaciones de archivo para una aplicación ClickOnce

1. Cree una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación normalmente o use la aplicación existente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. Abra el manifiesto de aplicación con un editor de texto o XML, como el Bloc de notas.

3. Busque el elemento `assembly` . Para más información, consulte [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).

4. Como elemento secundario del `assembly` elemento, agregue un `fileAssociation` elemento. El `fileAssociation` elemento tiene cuatro atributos:

   - `extension`: La extensión de nombre de archivo que desea asociar a la aplicación.

   - `description`: Una descripción del tipo de archivo, que aparecerá en el shell de Windows.

   - `progid`: Cadena que identifica de forma única el tipo de archivo, para marcarlo en el registro.

   - `defaultIcon`: Icono que se va a usar para este tipo de archivo. El icono debe agregarse como un recurso de archivo en el manifiesto de aplicación. Para obtener más información, vea [Cómo: Inclusión de un archivo de datos en una aplicación ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

     Para obtener un ejemplo de `file` los `fileAssociation` elementos y, vea [ \<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md).

5. Si desea asociar más de un tipo de archivo a la aplicación, agregue elementos `fileAssociation` adicionales. Tenga en cuenta `progid` que el atributo debe ser diferente para cada.

6. Una vez que haya terminado con el manifiesto de aplicación, vuelva a firmar el manifiesto. Puede hacerlo desde la línea de comandos mediante *Mage. exe*.

    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`

    Para más información, consulte [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="see-also"></a>Vea también
- [\<fileAssociation >, elemento](../deployment/fileassociation-element-clickonce-application.md)
- [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)
- [Mage.exe (Herramienta de generación y edición de manifiestos)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)