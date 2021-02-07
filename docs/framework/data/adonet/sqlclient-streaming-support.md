---
description: 'Daha fazla bilgi edinin: SqlClient akış desteği'
title: SqlClient Akış Desteği
ms.date: 03/30/2017
ms.assetid: c449365b-470b-4edb-9d61-8353149f5531
ms.openlocfilehash: 0f669f4a3c0b16a6b4a113c055a830c40fe3bdcf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766848"
---
# <a name="sqlclient-streaming-support"></a><span data-ttu-id="0ed45-103">SqlClient Akış Desteği</span><span class="sxs-lookup"><span data-stu-id="0ed45-103">SqlClient Streaming Support</span></span>

<span data-ttu-id="0ed45-104">SQL Server ile bir uygulama (.NET Framework 4,5 ' de yeni) arasında akış desteği, sunucuda (belgeler, görüntüler ve medya dosyaları) yapılandırılmamış verileri destekler.</span><span class="sxs-lookup"><span data-stu-id="0ed45-104">Streaming support between SQL Server and an application (new in .NET Framework 4.5) supports unstructured data on the server (documents, images, and media files).</span></span> <span data-ttu-id="0ed45-105">Bir SQL Server veritabanı ikili büyük nesneleri (blob) saklayabilir, ancak Blobların alınması çok fazla bellek kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="0ed45-105">A SQL Server database can store binary large objects (BLOBs), but retrieving BLOBS can use a lot of memory.</span></span>

<span data-ttu-id="0ed45-106">SQL Server akış desteği, verileri akışa almak zorunda kalmadan veri akışı yapan uygulamaların yazılmasını kolaylaştırır ve daha az bellek taşması özel durumu oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0ed45-106">Streaming support to and from SQL Server simplifies writing applications that stream data, without having to fully load the data into memory, resulting in fewer memory overflow exceptions.</span></span>

<span data-ttu-id="0ed45-107">Akış desteği, büyük Blobları göndermek, almak ve işlemek için, özellikle de iş nesnelerinin SQL Azure bağlanan senaryolarda, orta katman uygulamaların daha iyi ölçeklendirilmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0ed45-107">Streaming support will also enable middle-tier applications to scale better, especially in scenarios where business objects connect to SQL Azure in order to send, retrieve, and manipulate large BLOBs.</span></span>

> [!WARNING]
> <span data-ttu-id="0ed45-108">Bir uygulama `Context Connection` bağlantı dizesi anahtar sözcüğünü de kullanıyorsa, zaman uyumsuz çağrılar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0ed45-108">Asynchronous calls are not supported if an application also uses the `Context Connection` connection string keyword.</span></span>
>
> <span data-ttu-id="0ed45-109">Akışı desteklemek için eklenen üyeler, sorgulardan verileri almak ve sorguları ve saklı yordamlara parametreleri geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ed45-109">The members added to support streaming are used to retrieve data from queries and to pass parameters to queries and stored procedures.</span></span> <span data-ttu-id="0ed45-110">Akış özelliği temel OLTP ve veri geçiş senaryolarına yöneliktir ve şirket içi ve şirket dışı veri geçişleri ortamları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0ed45-110">The streaming feature addresses basic OLTP and data migration scenarios and is applicable to on-premises and off-premises data migrations environments.</span></span>

## <a name="streaming-support-from-sql-server"></a><span data-ttu-id="0ed45-111">SQL Server akış desteği</span><span class="sxs-lookup"><span data-stu-id="0ed45-111">Streaming Support from SQL Server</span></span>

<span data-ttu-id="0ed45-112">SQL Server akış desteği,, ve <xref:System.Data.Common.DbDataReader> <xref:System.Data.SqlClient.SqlDataReader> <xref:System.IO.Stream> <xref:System.Xml.XmlReader> nesneleri almak ve bunlara yanıt vermek için sınıflarında ve içindeki yeni işlevleri sunar <xref:System.IO.TextReader> .</span><span class="sxs-lookup"><span data-stu-id="0ed45-112">Streaming support from SQL Server introduces new functionality in the <xref:System.Data.Common.DbDataReader> and in the <xref:System.Data.SqlClient.SqlDataReader> classes in order to get <xref:System.IO.Stream>, <xref:System.Xml.XmlReader>, and <xref:System.IO.TextReader> objects and react to them.</span></span> <span data-ttu-id="0ed45-113">Bu sınıflar, sorgulardan verileri almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ed45-113">These classes are used to retrieve data from queries.</span></span> <span data-ttu-id="0ed45-114">Sonuç olarak, SQL Server adresinden akış desteği OLTP senaryolarından ve şirket içi ve şirket dışı ortamlar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0ed45-114">As a result, Streaming support from SQL Server addresses OLTP scenarios and applies to on-premises and off-premises environments.</span></span>

<span data-ttu-id="0ed45-115"><xref:System.Data.SqlClient.SqlDataReader>SQL Server 'den akış desteğini etkinleştirmek için aşağıdaki Üyeler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="0ed45-115">The following members were added to <xref:System.Data.SqlClient.SqlDataReader> to enable streaming support from SQL Server:</span></span>

1. <xref:System.Data.SqlClient.SqlDataReader.IsDBNullAsync%2A>

2. <xref:System.Data.SqlClient.SqlDataReader.GetFieldValue%2A?displayProperty=nameWithType>

3. <xref:System.Data.SqlClient.SqlDataReader.GetFieldValueAsync%2A>

4. <xref:System.Data.SqlClient.SqlDataReader.GetStream%2A>

5. <xref:System.Data.SqlClient.SqlDataReader.GetTextReader%2A>

6. <xref:System.Data.SqlClient.SqlDataReader.GetXmlReader%2A>

<span data-ttu-id="0ed45-116"><xref:System.Data.Common.DbDataReader>SQL Server 'den akış desteğini etkinleştirmek için aşağıdaki Üyeler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="0ed45-116">The following members were added to <xref:System.Data.Common.DbDataReader> to enable streaming support from SQL Server:</span></span>

1. <xref:System.Data.Common.DbDataReader.GetFieldValue%2A>

2. <xref:System.Data.Common.DbDataReader.GetStream%2A>

3. <xref:System.Data.Common.DbDataReader.GetTextReader%2A>

## <a name="streaming-support-to-sql-server"></a><span data-ttu-id="0ed45-117">SQL Server için akış desteği</span><span class="sxs-lookup"><span data-stu-id="0ed45-117">Streaming Support to SQL Server</span></span>

<span data-ttu-id="0ed45-118">SQL Server için akış desteği,, <xref:System.Data.SqlClient.SqlParameter> ve nesnelerini kabul etmek ve bunlara yanıt vermek için sınıfında yeni işlevsellik sunmaktadır <xref:System.Xml.XmlReader> <xref:System.IO.Stream> <xref:System.IO.TextReader> .</span><span class="sxs-lookup"><span data-stu-id="0ed45-118">Streaming support to SQL Server introduces new functionality in the <xref:System.Data.SqlClient.SqlParameter> class so it can accept and react to <xref:System.Xml.XmlReader>, <xref:System.IO.Stream>, and <xref:System.IO.TextReader> objects.</span></span> <span data-ttu-id="0ed45-119"><xref:System.Data.SqlClient.SqlParameter> , parametreleri sorgulara ve saklı yordamlara geçirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ed45-119"><xref:System.Data.SqlClient.SqlParameter> is used to pass parameters to queries and stored procedures.</span></span>

<span data-ttu-id="0ed45-120">Bir <xref:System.Data.SqlClient.SqlCommand> nesne veya çağrıyı elden atma <xref:System.Data.SqlClient.SqlCommand.Cancel%2A> tüm akış işlemlerini iptal etmelidir.</span><span class="sxs-lookup"><span data-stu-id="0ed45-120">Disposing a <xref:System.Data.SqlClient.SqlCommand> object or calling <xref:System.Data.SqlClient.SqlCommand.Cancel%2A> must cancel any streaming operation.</span></span> <span data-ttu-id="0ed45-121">Bir uygulama gönderirse <xref:System.Threading.CancellationToken> iptali garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="0ed45-121">If an application sends <xref:System.Threading.CancellationToken>, cancellation is not guaranteed.</span></span>

<span data-ttu-id="0ed45-122">Aşağıdaki <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> türler öğesinin bir kabul edileceği <xref:System.Data.SqlClient.SqlParameter.Value%2A> <xref:System.IO.Stream> :</span><span class="sxs-lookup"><span data-stu-id="0ed45-122">The following <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> types will accept a <xref:System.Data.SqlClient.SqlParameter.Value%2A> of <xref:System.IO.Stream>:</span></span>

- <span data-ttu-id="0ed45-123">**İkili**</span><span class="sxs-lookup"><span data-stu-id="0ed45-123">**Binary**</span></span>

- <span data-ttu-id="0ed45-124">**Ikili**</span><span class="sxs-lookup"><span data-stu-id="0ed45-124">**VarBinary**</span></span>

<span data-ttu-id="0ed45-125">Aşağıdaki <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> türler öğesinin bir kabul edileceği <xref:System.Data.SqlClient.SqlParameter.Value%2A> <xref:System.IO.TextReader> :</span><span class="sxs-lookup"><span data-stu-id="0ed45-125">The following <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> types will accept a <xref:System.Data.SqlClient.SqlParameter.Value%2A> of <xref:System.IO.TextReader>:</span></span>

- <span data-ttu-id="0ed45-126">**Char**</span><span class="sxs-lookup"><span data-stu-id="0ed45-126">**Char**</span></span>

- <span data-ttu-id="0ed45-127">**NChar**</span><span class="sxs-lookup"><span data-stu-id="0ed45-127">**NChar**</span></span>

- <span data-ttu-id="0ed45-128">**NVarChar**</span><span class="sxs-lookup"><span data-stu-id="0ed45-128">**NVarChar**</span></span>

- <span data-ttu-id="0ed45-129">**'Sini**</span><span class="sxs-lookup"><span data-stu-id="0ed45-129">**Xml**</span></span>

<span data-ttu-id="0ed45-130">**XML** <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> türü öğesinin bir kabul edileceği <xref:System.Data.SqlClient.SqlParameter.Value%2A> <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="0ed45-130">The **Xml**<xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> type will accept a <xref:System.Data.SqlClient.SqlParameter.Value%2A> of <xref:System.Xml.XmlReader>.</span></span>

<span data-ttu-id="0ed45-131"><xref:System.Data.SqlClient.SqlParameter.SqlValue%2A> , ve türündeki değerleri kabul <xref:System.Xml.XmlReader> edebilir <xref:System.IO.TextReader> <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="0ed45-131"><xref:System.Data.SqlClient.SqlParameter.SqlValue%2A> can accept values of type <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, and <xref:System.IO.Stream>.</span></span>

<span data-ttu-id="0ed45-132"><xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> Ve <xref:System.IO.Stream> nesnesi tarafından tanımlanan değere aktarılır <xref:System.Data.SqlClient.SqlParameter.Size%2A> .</span><span class="sxs-lookup"><span data-stu-id="0ed45-132">The <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, and <xref:System.IO.Stream> object will be transferred up to the value defined by the <xref:System.Data.SqlClient.SqlParameter.Size%2A>.</span></span>

## <a name="sample----streaming-from-sql-server"></a><span data-ttu-id="0ed45-133">Örnek--SQL Server akışı</span><span class="sxs-lookup"><span data-stu-id="0ed45-133">Sample -- Streaming from SQL Server</span></span>

<span data-ttu-id="0ed45-134">Örnek veritabanını oluşturmak için aşağıdaki Transact-SQL ' i kullanın:</span><span class="sxs-lookup"><span data-stu-id="0ed45-134">Use the following Transact-SQL to create the sample database:</span></span>

```sql
CREATE DATABASE [Demo]
GO
USE [Demo]
GO
CREATE TABLE [Streams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[textdata] NVARCHAR(MAX),
[bindata] VARBINARY(MAX),
[xmldata] XML)
GO
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'This is a test', 0x48656C6C6F, N'<test>value</test>')
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'Hello, World!', 0x54657374696E67, N'<test>value2</test>')
INSERT INTO [Streams] (textdata, bindata, xmldata) VALUES (N'Another row', 0x666F6F626172, N'<fff>bbb</fff><fff>bbc</fff>')
GO
```

<span data-ttu-id="0ed45-135">Örnek, aşağıdakilerin nasıl yapılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="0ed45-135">The sample shows how to do the following:</span></span>

- <span data-ttu-id="0ed45-136">Büyük dosyaları almak için zaman uyumsuz bir yol sağlayarak bir kullanıcı arabirimi iş parçacığını engellemeyi önleyin.</span><span class="sxs-lookup"><span data-stu-id="0ed45-136">Avoid blocking a user-interface thread by providing an asynchronous way to retrieve large files.</span></span>

- <span data-ttu-id="0ed45-137">SQL Server .NET Framework 4,5 ' de büyük bir metin dosyası aktarın.</span><span class="sxs-lookup"><span data-stu-id="0ed45-137">Transfer a large text file from SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="0ed45-138">Büyük bir XML dosyasını SQL Server .NET Framework 4,5 ' den aktarın.</span><span class="sxs-lookup"><span data-stu-id="0ed45-138">Transfer a large XML file from SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="0ed45-139">SQL Server verileri alın.</span><span class="sxs-lookup"><span data-stu-id="0ed45-139">Retrieve data from SQL Server.</span></span>

- <span data-ttu-id="0ed45-140">Büyük dosyaları (Blobları) bir SQL Server veritabanından başka bir veritabanına aktarma belleği olmadan.</span><span class="sxs-lookup"><span data-stu-id="0ed45-140">Transfer large files (BLOBs) from one SQL Server database to another without running out of memory.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading.Tasks;
using System.Xml;

namespace StreamingFromServer {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo";

      static void Main(string[] args) {
         CopyBinaryValueToFile().Wait();
         PrintTextValues().Wait();
         PrintXmlValues().Wait();
         PrintXmlValuesViaNVarChar().Wait();

         Console.WriteLine("Done");
      }

      // Application retrieving a large BLOB from SQL Server in .NET Framework 4.5 using the new asynchronous capability
      private static async Task CopyBinaryValueToFile() {
         string filePath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "binarydata.bin");

         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [bindata] FROM [Streams] WHERE [id]=@id", connection)) {
               command.Parameters.AddWithValue("id", 1);

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire BLOB into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  if (await reader.ReadAsync()) {
                     if (!(await reader.IsDBNullAsync(0))) {
                        using (FileStream file = new FileStream(filePath, FileMode.Create, FileAccess.Write)) {
                           using (Stream data = reader.GetStream(0)) {

                              // Asynchronously copy the stream from the server to the file we just created
                              await data.CopyToAsync(file);
                           }
                        }
                     }
                  }
               }
            }
         }
      }

      // Application transferring a large Text File from SQL Server in .NET Framework 4.5
      private static async Task PrintTextValues() {
         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [id], [textdata] FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire text document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.Write("{0}: ", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.Write("(NULL)");
                     }
                     else {
                        char[] buffer = new char[4096];
                        int charsRead = 0;
                        using (TextReader data = reader.GetTextReader(1)) {
                           do {
                              // Grab each chunk of text and write it to the console
                              // If you are writing to a TextWriter you should use WriteAsync or WriteLineAsync
                              charsRead = await data.ReadAsync(buffer, 0, buffer.Length);
                              Console.Write(buffer, 0, charsRead);
                           } while (charsRead > 0);
                        }
                     }

                     Console.WriteLine();
                  }
               }
            }
         }
      }

      // Application transferring a large Xml Document from SQL Server in .NET Framework 4.5
      private static async Task PrintXmlValues() {
         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();
            using (SqlCommand command = new SqlCommand("SELECT [id], [xmldata] FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire Xml Document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.WriteLine("{0}: ", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.WriteLine("\t(NULL)");
                     }
                     else {
                        using (XmlReader xmlReader = reader.GetXmlReader(1)) {
                           int depth = 1;
                           // NOTE: The XmlReader returned by GetXmlReader does NOT support async operations
                           // See the example below (PrintXmlValuesViaNVarChar) for how to get an XmlReader with asynchronous capabilities
                           while (xmlReader.Read()) {
                              switch (xmlReader.NodeType) {
                                 case XmlNodeType.Element:
                                    Console.WriteLine("{0}<{1}>", new string('\t', depth), xmlReader.Name);
                                    depth++;
                                    break;
                                 case XmlNodeType.Text:
                                    Console.WriteLine("{0}{1}", new string('\t', depth), xmlReader.Value);
                                    break;
                                 case XmlNodeType.EndElement:
                                    depth--;
                                    Console.WriteLine("{0}</{1}>", new string('\t', depth), xmlReader.Name);
                                    break;
                              }
                           }
                        }
                     }
                  }
               }
            }
         }
      }

      // Application transferring a large Xml Document from SQL Server in .NET Framework 4.5
      // This goes via NVarChar and TextReader to enable asynchronous reading
      private static async Task PrintXmlValuesViaNVarChar() {
         XmlReaderSettings xmlSettings = new XmlReaderSettings() {
            // Async must be explicitly enabled in the XmlReaderSettings otherwise the XmlReader will throw exceptions when async methods are called
            Async = true,
            // Since we will immediately wrap the TextReader we are creating in an XmlReader, we will permit the XmlReader to take care of closing\disposing it
            CloseInput = true,
            // If the Xml you are reading is not a valid document (as per <https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6bts1x50(v=vs.100)>) you will need to set the conformance level to Fragment
            ConformanceLevel = ConformanceLevel.Fragment
         };

         using (SqlConnection connection = new SqlConnection(connectionString)) {
            await connection.OpenAsync();

            // Cast the XML into NVarChar to enable GetTextReader - trying to use GetTextReader on an XML type will throw an exception
            using (SqlCommand command = new SqlCommand("SELECT [id], CAST([xmldata] AS NVARCHAR(MAX)) FROM [Streams]", connection)) {

               // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
               // Otherwise ReadAsync will buffer the entire Xml Document into memory which can cause scalability issues or even OutOfMemoryExceptions
               using (SqlDataReader reader = await command.ExecuteReaderAsync(CommandBehavior.SequentialAccess)) {
                  while (await reader.ReadAsync()) {
                     Console.WriteLine("{0}:", reader.GetInt32(0));

                     if (await reader.IsDBNullAsync(1)) {
                        Console.WriteLine("\t(NULL)");
                     }
                     else {
                        // Grab the row as a TextReader, then create an XmlReader on top of it
                        // We are not keeping a reference to the TextReader since the XmlReader is created with the "CloseInput" setting (so it will close the TextReader when needed)
                        using (XmlReader xmlReader = XmlReader.Create(reader.GetTextReader(1), xmlSettings)) {
                           int depth = 1;
                           // The XmlReader above now supports asynchronous operations, so we can use ReadAsync here
                           while (await xmlReader.ReadAsync()) {
                              switch (xmlReader.NodeType) {
                                 case XmlNodeType.Element:
                                    Console.WriteLine("{0}<{1}>", new string('\t', depth), xmlReader.Name);
                                    depth++;
                                    break;
                                 case XmlNodeType.Text:
                                    // Depending on what your data looks like, you should either use Value or GetValueAsync
                                    // Value has less overhead (since it doesn't create a Task), but it may also block if additional data is required
                                    Console.WriteLine("{0}{1}", new string('\t', depth), await xmlReader.GetValueAsync());
                                    break;
                                 case XmlNodeType.EndElement:
                                    depth--;
                                    Console.WriteLine("{0}</{1}>", new string('\t', depth), xmlReader.Name);
                                    break;
                              }
                           }
                        }
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="sample----streaming-to-sql-server"></a><span data-ttu-id="0ed45-141">Örnek--SQL Server akışı</span><span class="sxs-lookup"><span data-stu-id="0ed45-141">Sample -- Streaming to SQL Server</span></span>

<span data-ttu-id="0ed45-142">Örnek veritabanını oluşturmak için aşağıdaki Transact-SQL ' i kullanın:</span><span class="sxs-lookup"><span data-stu-id="0ed45-142">Use the following Transact-SQL to create the sample database:</span></span>

```sql
CREATE DATABASE [Demo2]
GO
USE [Demo2]
GO
CREATE TABLE [BinaryStreams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[bindata] VARBINARY(MAX))
GO
CREATE TABLE [TextStreams] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[textdata] NVARCHAR(MAX))
GO
CREATE TABLE [BinaryStreamsCopy] (
[id] INT PRIMARY KEY IDENTITY(1, 1),
[bindata] VARBINARY(MAX))
GO
```

<span data-ttu-id="0ed45-143">Örnek, aşağıdakilerin nasıl yapılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="0ed45-143">The sample shows how to do the following:</span></span>

- <span data-ttu-id="0ed45-144">Büyük bir BLOBUN SQL Server .NET Framework 4,5 ' de aktarılıyor.</span><span class="sxs-lookup"><span data-stu-id="0ed45-144">Transferring a large BLOB to SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="0ed45-145">Büyük bir metin dosyasını .NET Framework 4,5 ' de SQL Server aktarma.</span><span class="sxs-lookup"><span data-stu-id="0ed45-145">Transferring a large text file to SQL Server in .NET Framework 4.5.</span></span>

- <span data-ttu-id="0ed45-146">Büyük bir blobu aktarmak için yeni zaman uyumsuz özelliğini kullanma.</span><span class="sxs-lookup"><span data-stu-id="0ed45-146">Using the new asynchronous feature to transfer a large BLOB.</span></span>

- <span data-ttu-id="0ed45-147">Büyük bir blobu aktarmak için yeni zaman uyumsuz özelliği ve await anahtar sözcüğünü kullanma.</span><span class="sxs-lookup"><span data-stu-id="0ed45-147">Using the new asynchronous feature and the await keyword to transfer a large BLOB.</span></span>

- <span data-ttu-id="0ed45-148">Büyük bir BLOBUN aktarımı iptal ediliyor.</span><span class="sxs-lookup"><span data-stu-id="0ed45-148">Cancelling the transfer of a large BLOB.</span></span>

- <span data-ttu-id="0ed45-149">Yeni zaman uyumsuz özelliği kullanarak bir SQL Server diğerine akış.</span><span class="sxs-lookup"><span data-stu-id="0ed45-149">Streaming from one SQL Server to another using the new asynchronous feature.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading;
using System.Threading.Tasks;

namespace StreamingToServer {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo2;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo2";

      static void Main(string[] args) {
         CreateDemoFiles();

         StreamBLOBToServer().Wait();
         StreamTextToServer().Wait();

         // Create a CancellationTokenSource that will be cancelled after 100ms
         // Typically this token source will be cancelled by a user request (e.g. a Cancel button)
         CancellationTokenSource tokenSource = new CancellationTokenSource();
         tokenSource.CancelAfter(100);
         try {
            CancelBLOBStream(tokenSource.Token).Wait();
         }
         catch (AggregateException ex) {
            // Cancelling an async operation will throw an exception
            // Since we are using the Task's Wait method, this exception will be wrapped in an AggregateException
            // If you were using the 'await' keyword, the compiler would take care of unwrapping the AggregateException
            // Depending on when the cancellation occurs, you can either get an error from SQL Server or from .Net
            if ((ex.InnerException is SqlException) || (ex.InnerException is TaskCanceledException)) {
               // This is an expected exception
               Console.WriteLine("Got expected exception: {0}", ex.InnerException.Message);
            }
            else {
               // Did not expect this exception - re-throw it
               throw;
            }
         }

         Console.WriteLine("Done");
      }

      // This is used to generate the files which are used by the other sample methods
      private static void CreateDemoFiles() {
         Random rand = new Random();
         byte[] data = new byte[1024];
         rand.NextBytes(data);

         using (FileStream file = File.Open("binarydata.bin", FileMode.Create)) {
            file.Write(data, 0, data.Length);
         }

         using (StreamWriter writer = new StreamWriter(File.Open("textdata.txt", FileMode.Create))) {
            writer.Write(Convert.ToBase64String(data));
         }
      }

      // Application transferring a large BLOB to SQL Server in .NET Framework 4.5
      private static async Task StreamBLOBToServer() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            using (SqlCommand cmd = new SqlCommand("INSERT INTO [BinaryStreams] (bindata) VALUES (@bindata)", conn)) {
               using (FileStream file = File.Open("binarydata.bin", FileMode.Open)) {

                  // Add a parameter which uses the FileStream we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@bindata", SqlDbType.Binary, -1).Value = file;

                  // Send the data to the server asynchronously
                  await cmd.ExecuteNonQueryAsync();
               }
            }
         }
      }

      // Application transferring a large Text File to SQL Server in .NET Framework 4.5
      private static async Task StreamTextToServer() {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            await conn.OpenAsync();
            using (SqlCommand cmd = new SqlCommand("INSERT INTO [TextStreams] (textdata) VALUES (@textdata)", conn)) {
               using (StreamReader file = File.OpenText("textdata.txt")) {

                  // Add a parameter which uses the StreamReader we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@textdata", SqlDbType.NVarChar, -1).Value = file;

                  // Send the data to the server asynchronously
                  await cmd.ExecuteNonQueryAsync();
               }
            }
         }
      }

      // Cancelling the transfer of a large BLOB
      private static async Task CancelBLOBStream(CancellationToken cancellationToken) {
         using (SqlConnection conn = new SqlConnection(connectionString)) {
            // We can cancel not only sending the data to the server, but also opening the connection
            await conn.OpenAsync(cancellationToken);

            // Artificially delay the command by 100ms
            using (SqlCommand cmd = new SqlCommand("WAITFOR DELAY '00:00:00:100';INSERT INTO [BinaryStreams] (bindata) VALUES (@bindata)", conn)) {
               using (FileStream file = File.Open("binarydata.bin", FileMode.Open)) {

                  // Add a parameter which uses the FileStream we just opened
                  // Size is set to -1 to indicate "MAX"
                  cmd.Parameters.Add("@bindata", SqlDbType.Binary, -1).Value = file;

                  // Send the data to the server asynchronously
                  // Pass the cancellation token such that the command will be cancelled if needed
                  await cmd.ExecuteNonQueryAsync(cancellationToken);
               }
            }
         }
      }
   }
}
```

## <a name="sample----streaming-from-one-sql-server-to-another-sql-server"></a><span data-ttu-id="0ed45-150">Örnek--bir SQL Server başka bir SQL Server akış</span><span class="sxs-lookup"><span data-stu-id="0ed45-150">Sample -- Streaming From One SQL Server to Another SQL Server</span></span>

<span data-ttu-id="0ed45-151">Bu örnek, yük iptali desteğiyle, bir SQL Server büyük bir BLOBUN arasındaki zaman uyumsuz olarak nasıl akışa alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ed45-151">This sample demonstrates how to asynchronously stream a large BLOB from one SQL Server to another, with support for cancellation.</span></span>

```csharp
using System;
using System.Data;
using System.Data.SqlClient;
using System.IO;
using System.Threading;
using System.Threading.Tasks;

namespace StreamingFromServerToAnother {
   class Program {
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo2;Integrated Security=true"
      private const string connectionString = @"Server=(localdb)\V11.0;Database=Demo2";

      static void Main(string[] args) {
         // For this example, we don't want to cancel
         // So we can pass in a "blank" cancellation token
         E2EStream(CancellationToken.None).Wait();

         Console.WriteLine("Done");
      }

      // Streaming from one SQL Server to Another One using the new Async.NET
      private static async Task E2EStream(CancellationToken cancellationToken) {
         using (SqlConnection readConn = new SqlConnection(connectionString)) {
            using (SqlConnection writeConn = new SqlConnection(connectionString)) {

               // Note that we are using the same cancellation token for calls to both connections\commands
               // Also we can start both the connection opening asynchronously, and then wait for both to complete
               Task openReadConn = readConn.OpenAsync(cancellationToken);
               Task openWriteConn = writeConn.OpenAsync(cancellationToken);
               await Task.WhenAll(openReadConn, openWriteConn);

               using (SqlCommand readCmd = new SqlCommand("SELECT [bindata] FROM [BinaryStreams]", readConn)) {
                  using (SqlCommand writeCmd = new SqlCommand("INSERT INTO [BinaryStreamsCopy] (bindata) VALUES (@bindata)", writeConn)) {

                     // Add an empty parameter to the write command which will be used for the streams we are copying
                     // Size is set to -1 to indicate "MAX"
                     SqlParameter streamParameter = writeCmd.Parameters.Add("@bindata", SqlDbType.Binary, -1);

                     // The reader needs to be executed with the SequentialAccess behavior to enable network streaming
                     // Otherwise ReadAsync will buffer the entire BLOB into memory which can cause scalability issues or even OutOfMemoryExceptions
                     using (SqlDataReader reader = await readCmd.ExecuteReaderAsync(CommandBehavior.SequentialAccess, cancellationToken)) {
                        while (await reader.ReadAsync(cancellationToken)) {
                           // Grab a stream to the binary data in the source database
                           using (Stream dataStream = reader.GetStream(0)) {

                              // Set the parameter value to the stream source that was opened
                              streamParameter.Value = dataStream;

                              // Asynchronously send data from one database to another
                              await writeCmd.ExecuteNonQueryAsync(cancellationToken);
                           }
                        }
                     }
                  }
               }
            }
         }
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="0ed45-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ed45-152">See also</span></span>

- [<span data-ttu-id="0ed45-153">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0ed45-153">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
