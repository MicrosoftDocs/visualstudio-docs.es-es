---
title: Crear consultas de TableAdapter parametrizadas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 56e14d66275bd961829fc09e06f7d5e99dbcc2c4
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218904"
---
# <a name="create-parameterized-tableadapter-queries"></a>Crear consultas parametrizadas de TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Una consulta parametrizada devuelve datos que cumplen las condiciones de una cláusula WHERE dentro de la consulta. Por ejemplo, puede parametrizar una lista de clientes para mostrar solo los clientes de una determinada ciudad; para ello, agrega `WHERE City = @City` al final de la instrucción SQL que devuelve una lista de clientes.  
  
 Crear consultas parametrizadas de TableAdapter en el [Diseñador de Dataset](../data-tools/creating-and-editing-typed-datasets.md). También puede crear en una aplicación de Windows con el **parametrizar origen de datos** comando el **datos** menú. El **parametrizar origen de datos** comando crea los controles del formulario donde los valores de parámetro de entrada y ejecutar la consulta.  
  
> [!NOTE]
>  Al construir una consulta parametrizada, utilice la notación de parámetro que es específica de código se escribe en la base de datos. Por ejemplo, orígenes de datos de Access y OleDb utilizan el signo de interrogación '?' para denotar los parámetros, por lo que la cláusula WHERE tendría un aspecto similar al siguiente: `WHERE City = ?`.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de la configuración activa o la edición que está usando. Para cambiar la configuración, vaya a la **herramientas** menú y seleccione **importar y exportar configuraciones**. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-parameterized-tableadapter-query"></a>Crear una consulta de TableAdapter parametrizada  
  
#### <a name="to-create-a-parameterized-query-in-the-dataset-designer"></a>Para crear una consulta parametrizada en el Diseñador de Dataset  
  
-   Cree un nuevo TableAdapter y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL. Para obtener más información, consulte [crear y configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
     O bien  
  
-   Agregue una consulta a un TableAdapter existente, y agregue una cláusula WHERE con los parámetros deseados a la instrucción SQL. Para obtener más información, consulte [Cómo: crear consultas de TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
#### <a name="to-create-a-parameterized-query-while-designing-a-data-bound-form"></a>Para crear una consulta parametrizada durante el diseño de un formulario enlazado a datos  
  
1.  Seleccione en el formulario un control que ya esté enlazado a un conjunto de datos. Para obtener más información, consulte [controla el enlace Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  En el **datos** menú, seleccione**Agregar consulta**.  
  
3.  Completar la **generador de criterios de búsqueda** cuadro de diálogo, agregar una cláusula WHERE con los parámetros deseados a la instrucción SQL.  
  
### <a name="to-add-a-query-to-an-existing-data-bound-form"></a>Para agregar una consulta a un formulario enlazado a datos existente  
  
1. Abra el formulario en el **Diseñador de Windows Forms**.  
  
2. En el **datos** menú, seleccione **Agregar consulta** o **etiquetas inteligentes de datos**.  
  
   > [!NOTE]
   > Si **Agregar consulta** no está disponible en el **datos** menú, seleccione un control en el formulario que muestra el origen de datos quiera agregar parametrización. Por ejemplo, si el formulario muestra datos en un control <xref:System.Windows.Forms.DataGridView>, selecciónelo. Si el formulario muestra datos en controles individuales, seleccione un control enlazado a datos.  
  
3. En el **tabla de origen de datos seleccione** área, seleccione la tablethat que quiere agregar parametrización.  
  
4. Escriba un nombre en el **nuevo nombre de consulta** cuadro Si va a crear una nueva consulta.  
  
    O bien  
  
    Seleccione una consulta en el **nombre de consulta existente** cuadro.  
  
5. En el **texto de la consulta** , escriba una consulta que toma parámetros.  
  
6. Seleccione **Aceptar**.  
  
    Un control para el parámetro de entrada y un **carga** botón se agregan al formulario en un <xref:System.Windows.Forms.ToolStrip> control.  
  
   Parámetros de TableAdapter se pueden asignar valores null cuando desea consultar registros que no tienen ningún valor actual. Por ejemplo, considere la consulta siguiente que tiene un `ShippedDate` parámetro en su `WHERE` cláusula:  
  
   `SELECT CustomerID, OrderDate, ShippedDate`  
  
   `FROM Orders`  
  
   `WHERE (ShippedDate = @ShippedDate) OR`  
  
   `(ShippedDate IS NULL)`  
  
   Si se tratara de una consulta en un TableAdapter, podría consultar todos los pedidos que no se han enviado por el código siguiente:  
  
   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]  
  
#### <a name="to-enable-a-query-to-accept-null-values"></a>Para habilitar una consulta que acepte valores null  
  
1.  En el **Diseñador de Dataset**, seleccione la consulta de TableAdapter que debe aceptar los valores de parámetro null.  
  
2.  En el **propiedades** ventana, seleccione **parámetros**. A continuación, presione el botón de puntos suspensivos (**...** ) para abrir el **Editor de la colección de parámetros**.  
  
3.  Seleccione el parámetro que permite valores null y establezca el **AllowDbNull** propiedad `true`.  
  
## <a name="see-also"></a>Vea también  
 [Llenar conjuntos de datos mediante TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

