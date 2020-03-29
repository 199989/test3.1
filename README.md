# test3.1
@@ -8,7 +8,6 @@ public Sudoku(int[][] matrix, int rank) {
    }

    public static void main(String[] args) {
        // 号称世界上最难数独
        int[][] sudoku = {
        		{0,2,0,0},
        		{0,0,0,4},
            
            
            
            
            
            import java.io.*;
import java.util.LinkedList;

public class TxtReadWriter {

    public static void main(String args[]) {
        readFile("input.txt");
        writeFile("output.txt");
        int[] array = readFile("input.txt");
        LinkedList<int[][]> sudokus = splitArray(array, 9, 2);
        writeFile("output.txt", sudokus, 9);

    }

    /**
     * 读入TXT文件
     * 返回一个整型数组包含里面所有数字
     */
    public static void readFile( String pathName) {
        // 绝对路径或相对路径都可以，写入文件时演示相对路径,读取以上路径的input.txt文件
        //防止文件建立或读取失败，用catch捕捉错误并打印，也可以throw;
        //不关闭文件会导致资源的泄露，读写文件都同理
        //Java7的try-with-resources可以优雅关闭文件，异常时自动关闭文件；详细解读https://stackoverflow.com/a/12665271
    public static int[] readFile( String pathName) {
    	int[] array = new int[5000];
    	int count = 0;

        try {
        	FileReader reader = new FileReader(pathName);
            BufferedReader br = new BufferedReader(reader);
            String line;
            while ((line = br.readLine()) != null) {
                // 一次读入一行数据
                System.out.println(line);
            int number = 0;

            while ((number = br.read()) != -1) {
            	if((number-48) >= 0) {
            		array[count++] = number - 48;
            	}
            }
            br.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
        return array;
    }

    /**
     * 写入TXT文件
     */
    public static void writeFile(String pathName) {
        try {
            File writeName = new File(pathName); // 相对路径，如果没有则要建立一个新的output.txt文件
            writeName.createNewFile(); // 创建新文件,有同名的文件的话直接覆盖
            try (FileWriter writer = new FileWriter(writeName);
                 BufferedWriter out = new BufferedWriter(writer)
            ) {
                out.write("我会写入文件啦1\r\n");
                out.write("我会写入文件啦2\r\n");
                out.flush(); // 把缓存区内容压入文件
            }
    public static void writeFile(String pathName, LinkedList<int[][]> sudokus, int rank) {

    	try {
            File writeName = new File(pathName); 
            writeName.createNewFile(); 
            FileWriter writer = new FileWriter(writeName);
		    BufferedWriter out = new BufferedWriter(writer);

		    for(int k = 0; k < sudokus.size(); k++) {
		    	int[][] array = new int[9][9];
		    	array = sudokus.get(k);
		    	for(int i = 0; i < rank; i++) {
		    		for(int j = 0; j < rank; j++) {
		    			out.write(array[i][j] + 48);
		    			out.write(" ");
		    		}
		    		out.write("\n");
		    	}
		    	out.write("\n");
		    }
    out.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
	    }
    }

    /**
     * 将整型readerFile读出的数组分解为不同盘面
     * 用LinkedList进行存储二位数组
     * 返回一个LinkedList
     * param suCnt面数
     * param rank阶数
     */
    public static LinkedList<int[][]> splitArray(int[] array, int rank, int suCnt) {
    	LinkedList<int[][]> sudokus = new LinkedList<int[][]>();
    	int count = 0;
    	for(int k = 0; k < suCnt; k++) {
    		int[][] temp = new int[9][9];
	    	for(int i = 0; i < rank; i++) {
	    		for(int j = 0; j < rank; j++) {
	    			temp[i][j] = array[count++];
	    		}
	    	}
	    	sudokus.add(temp);
    	}

    	return sudokus;
    }


    public static void printArray(int[][] array, int rank) {
    	for(int i = 0; i < rank; i++) {
    		for(int j = 0; j < rank; j++) {
    			System.out.print(array[i][j]);
    		}
    		System.out.print("\n");
    	}
    }







}
