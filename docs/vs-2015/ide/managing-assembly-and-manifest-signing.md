---
title: Administrar la firma de ensamblados y manifiestos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ab8ab81c83f98a7a35620db7cbb10a0f700d78e4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172749"
---
# <a name="managing-assembly-and-manifest-signing"></a>Administrar la firma de ensamblados y manifiestos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La firma de nombre seguro ofrece una identidad única a un componente de software. Los nombres seguros se usan para garantizar que otra persona no puede suplantar la identidad del ensamblado y para garantizar que las dependencias de componente e instrucciones de configuración se asignan al componente y a la versión del componente correctos.  
  
 Un nombre seguro se compone de la identidad del ensamblado (nombre de texto simple, número de versión e información sobre referencia cultural), más un token de clave pública y una firma digital.  
  
 Para obtener información sobre cómo firmar ensamblados en proyectos de Visual Basic y C#, consulte [Crear y utilizar ensamblados con nombre seguro](http://msdn.microsoft.com/library/ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9).  
  
 Para obtener información sobre cómo firmar ensamblados en proyectos de Visual C++, consulte [Ensamblados de nombre seguro (Firma de ensamblados) (C++/CLI)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc).  
  
## <a name="asset-types-and-signing"></a>Tipos de recursos y firma  
 Puede firmar manifiestos de aplicación y ensamblados .NET. Entre ellas se incluyen las siguientes:  
  
-   archivos ejecutables (.exe)  
  
-   manifiestos de aplicación (.exe.manifest)  
  
-   manifiestos de implementación (.application)  
  
-   ensamblados de componente compartido (.dll)  
  
 Debe firmar los siguientes tipos de recurso:  
  
1.  Ensamblados, si quiere implementarlos en la caché global de ensamblados (GAC).  
  
2.  Manifiestos de implementación y aplicación [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Visual Studio permite firmar de manera predeterminada estas aplicaciones.  
  
3.  Los ensamblados de interoperabilidad primarios, que se usan para la interoperabilidad COM. La utilidad TLBIMP exige nombres seguros al crear un ensamblado de interoperabilidad primario de una biblioteca de tipos COM.  
  
 En general, no debería firmar archivos ejecutables. Un componente con nombre seguro no puede hacer referencia a un componente con nombre no seguro que se implementa con la aplicación. Visual Studio no firma los archivos ejecutables de aplicaciones, pero en su lugar firma el manifiesto de aplicación, que señala al archivo ejecutable de nombre no seguro. Se recomienda evitar firmar componentes que son privados para la aplicación, porque si los firma puede ser más difícil administrar las dependencias.  
  
## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Cómo firmar un ensamblado en Visual Studio  
 Puede firmar una aplicación o componente mediante la pestaña **Firma** de la ventana Propiedades del proyecto (haga clic con el botón derecho en el nodo del proyecto en el **Explorador de soluciones** y seleccione **Propiedades**, escriba las **propiedades del proyecto** en la ventana **Inicio rápido** o pulse ALT + ENTRAR en la ventana **Explorador de soluciones**). En la pestaña **Firma**, active la casilla **Firmar el ensamblado**.  
  
 Especifique un archivo de clave. Si decide crear un nuevo archivo de clave, tenga en cuenta que los nuevos archivos de clave se crean siempre en el formato .pfx. Necesita un nombre y una contraseña para el nuevo archivo.  
  
> [!WARNING]
>  Siempre debe proteger el archivo de clave con una contraseña para evitar que otra persona lo use. También puede proteger las claves mediante proveedores o almacenes de certificados.  
  
 También puede señalar a una clave que ya ha creado. Para obtener más información sobre la creación de claves, consulte [Cómo: Crear un par de claves privada y pública](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114).  
  
 Si tiene acceso solo a una clave pública, puede usar Retrasar la firma para aplazar la asignación de la clave. Para habilitar Retrasar la firma, active la casilla **Retrasar firma solo**. Un proyecto con retraso de firma no se ejecutará y no lo podrá depurar. En cambio, puede omitir la comprobación durante el desarrollo al usar [Sn.exe (Herramienta de nombre seguro)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) con la opción `-Vr`.  
  
 Para obtener información sobre cómo firmar manifiestos, consulte [Cómo: Firmar aplicaciones y manifiestos de implementación](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
## <a name="see-also"></a>Vea también  
 [Ensamblados con nombre seguro](http://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)   
 [Ensamblados de nombre seguro (Firma de ensamblados) (C++/CLI)](http://msdn.microsoft.com/library/c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc)



