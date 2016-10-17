# NoteDaily
＃android android.permission.READ_LOGS

System.out.println("--------func start--------"); // 方法启动
        BufferedReader bufferedReader = null;
        BufferedWriter writer = null;
        try
        {
            ArrayList<String> cmdLine=new ArrayList<String>();   //设置命令   logcat -d 读取日志
            cmdLine.add("logcat");
            cmdLine.add("-d");

            ArrayList<String> clearLog=new ArrayList<String>();  //设置命令  logcat -c 清除日志
            clearLog.add("logcat");
            clearLog.add("-c");

            Process process=Runtime.getRuntime().exec(cmdLine.toArray(new String[cmdLine.size()]));   //捕获日志
            bufferedReader=new BufferedReader(new InputStreamReader(process.getInputStream()));    //将捕获内容转换为BufferedReader
            File file = new File(Environment.getExternalStorageDirectory(),
                    "LogError_all.log");
            writer = new BufferedWriter(new FileWriter(file, true));
//                Runtime.runFinalizersOnExit(true);
            String str=null;
            while((str=bufferedReader.readLine())!=null)    //开始读取日志，每次读取一行
            {
                Runtime.getRuntime().exec(clearLog.toArray(new String[clearLog.size()]));  //清理日志....这里至关重要，不清理的话，任何操作都将产生新的日志，代码进入死循环，直到bufferreader满
//                System.out.println(str);    //输出，在logcat中查看效果，也可以是其他操作，比如发送给服务器..
                writer.append(DateUtil.getDateTime(System.currentTimeMillis())).append("---").append(str).append("\n");
            }
            if(str==null)
            {
                System.out.println("--   is null   --");
            }
        }
        catch(Exception e)
        {
            e.printStackTrace();
        }
        finally {
            if (bufferedReader != null) {
                try {
                    bufferedReader.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            if (writer != null) {
                try {
                    writer.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
        System.out.println("--------func end--------");
