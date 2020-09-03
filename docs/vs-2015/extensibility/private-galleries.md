---
title: Galerías privadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX galleries, private
- private galleries, VSIX
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 895fbef5459de75c7ccdc6a090fc30ec27a030f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444926"
---
# <a name="private-galleries"></a>Private Galleries
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede compartir los controles, las plantillas y las herramientas que desarrolle mediante su publicación en una *galería privada* de la intranet de la organización, como se indica a continuación:  
  
- Cree una fuente Atom (RSS) en una ubicación central (repositorio) configurada adecuadamente en la intranet. Para obtener más información, consulte [Cómo: crear una fuente Atom para una galería privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
- Distribuya un archivo. pkgdef que describa la galería privada. Se recomienda esta configuración para los administradores que deseen conectar una galería privada a muchos equipos al mismo tiempo.  
  
## <a name="adding-a-private-gallery-to-extensions-and-updates-in-visual-studio"></a>Agregar una galería privada a extensiones y actualizaciones en Visual Studio  
 Cuando una galería privada está disponible, puede agregarla a **extensiones y actualizaciones** en Visual Studio.  
  
 ![Cuadro de diálogo para agregar del Administrador de extensiones](../extensibility/media/em-adddialog.png "EM_AddDialog")  
  
#### <a name="to-add-a-private-gallery-to-extensions-and-updates"></a>Para agregar una galería privada a extensiones y actualizaciones  
  
1. En la barra de menús, elija **herramientas**, **Opciones**.  
  
2. En el nodo **entorno** , seleccione **extensiones y actualizaciones**.  
  
3. Elija el botón **Agregar**.  
  
4. En el campo **nombre** , escriba un nombre para la galería privada, por ejemplo, `My Gallery` .  
  
5. En el campo **dirección URL** , escriba la dirección URL de la fuente Atom o el sitio de SharePoint que hospeda la galería privada.  
  
    1. Si el host es una fuente Atom que se conecta a la galería privada, la dirección URL sería similar a esta: `http://www.mywebsite/mygallery/atom.xml` .  Esta dirección URL puede hacer referencia a un archivo o una ruta de acceso de red.  
  
    2. Si el host es un sitio de SharePoint, la dirección URL sería similar a esta: `http://mysharepoint/sites/mygallery/forms/AllItems.aspx` .  
  
### <a name="managing-private-galleries"></a>Administrar galerías privadas  
 Un administrador puede hacer que una galería privada esté disponible para varios equipos al mismo tiempo modificando el registro del sistema en cada equipo. Para ello, cree un archivo. pkgdef que describa las nuevas claves del registro y sus valores.  El formato de este archivo es el siguiente.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Para obtener más información, vea [Cómo: administrar una galería privada mediante la configuración del registro](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## <a name="installing-extensions-from-a-private-gallery"></a>Instalación de extensiones desde una galería privada  
 Puede buscar e instalar extensiones de Visual Studio desde una galería privada en **extensiones y actualizaciones**. En los pasos siguientes se usa una galería privada denominada `My Gallery` .  
  
 ![Administrador de extensiones instalando una galería privada](../extensibility/media/em.png "EM_")  
  
#### <a name="to-search-for-and-install-extensions-from-a-private-gallery"></a>Para buscar e instalar las extensiones desde una galería privada  
  
1. En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2. En el panel izquierdo, seleccione **extensiones en línea**y, a continuación, seleccione **mi Galería**.  
  
3. En el panel derecho, seleccione una extensión y, a continuación, elija el botón **Descargar** .  
  
## <a name="updating-extensions-from-a-private-gallery"></a>Actualización de extensiones desde una galería privada  
 A medida que se publican nuevas versiones de las extensiones de Visual Studio en la galería privada, puede actualizar las extensiones que ha instalado. En los pasos siguientes se usa una galería privada denominada `My Repository` .  
  
 ![Actualización de la galería privada del Administrador de extensiones](../extensibility/media/em-update.png "EM_Update")  
  
#### <a name="to-update-an-installed-extension-from-a-private-gallery"></a>Para actualizar una extensión instalada desde una galería privada  
  
1. En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2. En el panel izquierdo, seleccione **actualizaciones**y, a continuación, seleccione **mi repositorio**.  
  
3. En el panel derecho, seleccione una extensión y, a continuación, elija el botón **Actualizar** .  
  
## <a name="see-also"></a>Consulte también  
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Suministro de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
