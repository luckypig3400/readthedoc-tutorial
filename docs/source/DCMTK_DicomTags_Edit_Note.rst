{%hackmd theme-dark %}

DCMTK-Dicom影像編輯與傳輸工具
=============================

DCMTK (DICOM ToolKit)

目錄
----

[TOC]

DCMTK網站資源
-------------

DCMTK官網
~~~~~~~~~

-  https://www.dcmtk.org/en/ ### 很詳細的使用教學
-  https://officeguide.cc/ubuntu-linux-dcmtk-dicom-toolkit-tutorial-examples/

安裝DCMTK
---------

DCMTK官方安裝手冊
~~~~~~~~~~~~~~~~~

-  https://github.com/DCMTK/dcmtk/blob/master/INSTALL

也可以下載別人build好的可執行檔(zip)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  `dicom.offis.de DCMTK
   Binary <https://dicom.offis.de/dcmtk.php.en#bin>`__

或是透過Chocolatey安裝 dicom.offis.de 建置好的DCMTK
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  `Chocolatey官方社群安裝教學 <https://community.chocolatey.org/courses/installation/installing?method=installing-chocolatey>`__
-  `[Chocolatey] Windows 套件管理工具 - Chocolatey
   初體驗 <https://marcus116.blogspot.com/2019/02/chocolatey-windows-chocolatey.html>`__

確定Chocolatey安裝好後即可透過以下指令安裝DCMTK
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

::

   choco install dcmtk

--------------

使用DCMTK傳輸Dicom影像
----------------------

DCMTK官方dicom影像傳輸指引
~~~~~~~~~~~~~~~~~~~~~~~~~~

-  https://support.dcmtk.org/docs/dcmsend.html

   e.g., dcmsend -v -aet {your AE} -aec {EBM AE} {EBM PACS IP} {{PRT}
   PRFile

連中岳老師解說
~~~~~~~~~~~~~~

要手動上傳DICOM影像，可於cmd執行

.. code:: bash!

   dcmsend -v +sd +r -aet XXSCU -aec DCM4CHEE 127.0.0.1 11112 {DICOM檔目錄}

自行實測結果-(從Windows10傳送到Local DCM4CHEE)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: bash!

   dcmsend -v +sd +r -aec DCM4CHEE 127.0.0.1 11112 {DICOM檔目錄}

.. container:: info

   省略-aet參數亦可正常傳輸dicom影像

自行實測結果-(從Windows10傳送到自架遠端DCM4CHEE)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: bash!

   dcmsend -v +sd +r -aet XXSCU -aec DCM4CHEE dcm4chee.luckypig.net 11112 ${dicom-image-folder}

透過以下網址查詢上傳的資料
^^^^^^^^^^^^^^^^^^^^^^^^^^

-  http://dcm4chee.luckypig.net:8080/dcm4chee-arc/ui2/
-  http://dcm4chee.luckypig.net:81/bluelight/search/html/start.html

自行實測結果-(從Windows10傳送到Local ORTHANC)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code:: bash!

   dcmsend -v +sd +r -aet XXSCU -aec ORTHANC 127.0.0.1 4242 {DICOM檔目錄}

..

   REF: https://book.orthanc-server.com/users/cookbook.html

--------------

Dicom影像標記資訊(Dicom Image Tags)
-----------------------------------

Dicom完整欄位資訊
~~~~~~~~~~~~~~~~~

-  https://dicom.innolitics.com/ciods/

單張超音波(UltraSound)完整Dicom Tags
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

-  https://dicom.innolitics.com/ciods/us-image

柏勳目前有實作的Dicom Tags
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. image:: https://i.imgur.com/o0LCLyn.png

整理必填Dicom欄位資料
~~~~~~~~~~~~~~~~~~~~~
