---
title: "Página Firma, Diseñador de proyectos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 34
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4669932307d37593154e337265288919a1042f37
ms.lasthandoff: 02/22/2017

---
# <a name="signing-page-project-designer"></a>Página Firma, Diseñador de proyectos
Use la página **Firma** del **Diseñador de proyectos** para firmar los manifiestos de aplicación e implementación y también para firmar el ensamblado (firma con nombre seguro).  
  
 Tenga en cuenta que la firma de manifiestos de aplicación e implementación es un proceso distinto al de la firma de un ensamblado, aunque ambas tareas se realicen en la página **Firma**.  
  
 Además, el almacenamiento de información de archivo de clave es diferente para la firma de manifiestos y la firma de ensamblados. En la firma de manifiestos, la información de clave se almacena en la base de datos de almacenamiento criptográfico del equipo y el almacén de certificados de Windows del usuario actual. En la firma de ensamblados, la información de clave se almacena únicamente en la base de datos de almacenamiento criptográfico del equipo.  
  
 Para acceder a la página **Firma**, seleccione un nodo de proyecto en el **Explorador de soluciones** y, después, en el menú **Proyecto**, haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos**, haga clic en la pestaña **Firma**.  
  
## <a name="application-and-deployment-manifest-signing"></a>Firma de manifiestos de aplicación e implementación  
 Casilla **Firmar los manifiestos de ClickOnce**  
 Active esta casilla para firmar los manifiestos de aplicación e implementación con un par de claves pública y privada. Para más información sobre cómo hacerlo, vea [Cómo: Firmar aplicaciones y manifiestos de implementación](../../ide/how-to-sign-application-and-deployment-manifests.md).  
  
 Botón **Seleccionar de almacén**  
 Permite seleccionar un certificado existente desde el almacén de certificados personales del usuario actual. Puede seleccionar uno de estos certificados para firmar los manifiestos de aplicación e implementación.  
  
 Haga clic en **Seleccionar de almacén** para abrir el cuadro de diálogo **Seleccionar un certificado**, donde se muestran los certificados del almacén de certificados personal que son válidos en la actualidad (no expirados) y que tienen claves privadas. El propósito del certificado seleccionado debe incluir la firma de código.  
  
 Si hace clic en **Ver propiedades del certificado**, aparece el cuadro de diálogo **Detalles del certificado**. Este cuadro de diálogo incluye información detallada sobre el certificado y opciones adicionales. Puede hacer clic en **Más información sobre certificados** para ver información adicional de la Ayuda.  
  
 Botón **Seleccionar de archivo**  
 Permite seleccionar un certificado desde un archivo de clave existente.  
  
 Haga clic en **Seleccionar de archivo** para abrir el cuadro de diálogo **Seleccionar archivo**, que permite seleccionar un archivo de clave de certificado (.pfx). El archivo debe estar protegido mediante contraseña y aún no puede estar en el almacén de certificados personal.  
  
 En el cuadro de diálogo **Escribir contraseña para abrir archivo**, escriba una contraseña para abrir el archivo de clave de certificado (.pfx). La información de contraseña se almacena en la lista del contenedor de claves personal y en el almacén de certificados personal.  
  
 Botón **Crear certificado de prueba**  
 Permite crear un certificado para pruebas. El certificado de prueba se usa para firmar los manifiestos de aplicación e implementación de ClickOnce.  
  
 Haga clic en **Crear certificado de prueba** para abrir el cuadro de diálogo **Crear certificado de prueba**, donde puede escribir una contraseña para el archivo de clave con nombre seguro del certificado de prueba. El archivo se denomina *nombreDeProyecto*_TemporaryKey.pfx. Si hace clic en **Aceptar** sin escribir una contraseña, el archivo .pfx no se cifra con contraseña.  
  
 Cuadro **Dirección URL del servidor de marca de tiempo**  
 Especifica la dirección de un servidor que marca la firma con un tiempo. Si se proporciona un certificado, este sitio externo comprueba la hora en que se ha firmado la aplicación.  
  
## <a name="assembly-signing"></a>Firma de ensamblados  
 Casilla **Firmar el ensamblado**  
 Active esta casilla para firmar el ensamblado y crear un archivo de clave con nombre seguro. Para más información sobre la firma del ensamblado mediante el **Diseñador de proyectos**, vea [Cómo: Firmar un ensamblado (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 Esta opción usa la herramienta Al.exe proporcionada por [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] para firmar el ensamblado. Para más información sobre Al.exe, vea [Cómo: Firmar un ensamblado con un nombre seguro](http://msdn.microsoft.com/Library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 Lista **Elija un archivo de clave de nombre seguro**  
 Permite especificar un archivo de clave con nombre seguro nuevo o existente para firmar el ensamblado. Seleccione **\<Examinar... >** para seleccionar un archivo de clave existente.  
  
 Seleccione **\<Nuevo... >** para crear un nuevo archivo de clave para firmar el ensamblado. Aparece el cuadro de diálogo **Crear clave de nombre seguro**, que se puede usar para especificar un nombre de archivo de clave y proteger el archivo de clave con una contraseña. La contraseña debe tener al menos 6 caracteres. Si especifica una contraseña, se crea un archivo de intercambio de información personal (.pfx); si no especifica ninguna contraseña, se crea un archivo de clave con nombre seguro (.snk).  
  
 Botón **Cambiar contraseña**  
 Cambia la contraseña del archivo de clave de intercambio de información personal (.pfx) usado para firmar el ensamblado.  
  
 Haga clic en **Cambiar contraseña** para abrir el cuadro de diálogo **Cambiar contraseña de clave**. En este cuadro de diálogo, **Contraseña anterior** es la contraseña actual del archivo de clave. **Nueva contraseña** debe tener al menos 6 caracteres. La información de contraseña se almacena en el almacén de certificados de Windows del usuario actual.  
  
 Casilla **Retrasar firma solo**  
 Active esta casilla para habilitar la firma retardada.  
  
 Tenga en cuenta que un proyecto con firma retardada no se ejecutará y no se puede depurar. Pero puede usar [Sn.exe (Herramienta de nombre seguro)](http://msdn.microsoft.com/Library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6) con la opción `-Vr` para omitir la comprobación durante el desarrollo.  
  
> [!NOTE]
>  Al firmar un ensamblado, es posible que no siempre tenga acceso a una clave privada. Por ejemplo, una organización podría tener un par de claves muy bien guardado al que los desarrolladores no tuvieran acceso cada día. La clave pública podría estar disponible, pero el acceso a la clave privada estaría restringido a algunas personas. En tal caso, podría usar la *firma retardada* o la *firma parcial* para proporcionar la clave pública, retrasando la adición de la clave privada hasta la entrega del ensamblado.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [Administrar la firma de ensamblados y manifiestos](../../ide/managing-assembly-and-manifest-signing.md)   
 [Firma de nombre seguro para aplicaciones administradas](http://msdn.microsoft.com/en-us/5fef3490-c519-4363-94fd-8b1ad260dab5)   
 [Cómo: Firmar aplicaciones y manifiestos de implementación](../../ide/how-to-sign-application-and-deployment-manifests.md)   
 [Cómo: Firmar un ensamblado (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Cómo: Firmar un ensamblado con un nombre seguro](http://msdn.microsoft.com/Library/2c30799a-a826-46b4-a25d-c584027a6c67)   
 [Ensamblados con nombre seguro](http://msdn.microsoft.com/Library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b)
