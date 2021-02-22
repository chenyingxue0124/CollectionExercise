数学では、collectionという概念はよく出てきます。
コレクションはいくつかの対象を持つものです。
javaでは、同じ用途で利用する複数の値を格納していく時に、javaでよく使用するものを紹介します

**■配列**

配列は同じ用途で利用する複数の値を格納しておく時に使用されます。
例えば10個の値を保存する場合、変数を使う場合は変数が10個必要ですが、配列では10個の要素を持つ1つの配列に値を保存します。また繰り返し処理を使って順に値を取り出すといったことができます。

学生五人の成績を入力する際に、配列を使わないと

     public class ArrayExercise {
    	 public static void main (String[] args) {
    		    int n1 = 68;
    	        int n2 = 79;
    	        int n3 = 91;
    	        int n4 = 85;
    	        int n5 = 62;
    	        System.out.println(n1);s
    	        System.out.println(n2);
    	        System.out.println(n3);
    	        System.out.println(n4);
    	        System.out.println(n5);        
    		 }
    }

配列を使用するには、まず配列を宣言します。配列の宣言は以下のように記述します。

    型名[] 配列変数名;

一つの配列に確保される一つ一つの場所を要素と呼びます。
new演算子では型名の後の「[」から「]」の間に要素の数である要素数を指定して格納する場所である要素を確保し、それを配列変数に代入します。これで配列は要素数の数だけの値を格納することができるようになります。

    型名 配列変数名[];
    配列変数名 = new 型名[要素数];

以下の書き方もできます。

    型名 配列変数名[] = new 型名[要素数];

学生五人の成績を入力するために、要素数は5です。

    int ns[] = new int[5];

一つの配列には同じデータ型の値しか格納することはできません。
配列を作成した後に、サーズを変更できません。

    ns[0] = 68;

初期値の代入を次のように記述することができます。

    int ns[] = { 68, 79, 91, 85, 62 };

配列の各要素は次のように表すことができます。

    配列変数[インデックス]

例えば5個の要素を持つ配列を作成した場合にはインデックスとして0から4までを使用して各要素を表すことができます。1から5ではなく0から始まることに注意して下さい。

    public static void main(String[] args) {
        int ns[] = new int[] { 68, 79, 91, 85, 62 };
        System.out.println(ns[3]);
        for (int i=0; i<5; i++) {
        	System.out.println(ns[i]); 
        }      
    }

    public static void main(String[] args) {
        int ns[] = new int[] { 68, 79, 91, 85, 62 };
        System.out.println(ns[3]);
        for (int i=0; i<5; i++) {
        	System.out.println("普通forループ"+ns[i]); 
        }      
        for(int i:ns) {
        	System.out.println("拡張for文"+i);
        }
    }

配列で確保されている要素の数を調べたい場合があります。
要素の数は配列の長さとも呼ばれますが次の書式で取得することができます。

    配列変数名.length
    public static void main(String[] args) {
        int ns[] = new int[] { 68, 79, 91, 85, 62 };
        System.out.println(ns[3]);      
        for(int i=0; i<ns.length;i++) {
        	System.out.println(i);
        }
    }

配列には次のような制限があります。
**１．初期化後に配列のサイズを変更することはできません。<br>
２．配列はインデックス順にしかアクセスできません。**

なので、javaのpackage java.utilに、**List,Set,Map**という配列と違ってコレクションがあります。

**■List**
重複した要素を含むことができる順序の付けられたコレクション。
配列だけは入れ物の大きさを決めなければならない。一度配列の大きさを決めると、それ以後変更できません。
一方、Listは要素の大きさは可変です。

    String list[] = new String[3];
    List<String> list = new ArrayList<String>();

配列は固定の大きさなので、追加・削除・検索はできない。
しかし、Listは可変であるので、要素をどんどん追加できるし、削除もできる。

よく使っているmethod：<br>
**・Listの最後に要素を追加**<br>
　list.add("A");<br>
**・指定した位置に、要素を追加**<br>
　list.add(index,"A");<br>
**・要素の取得**<br>
　list.get(index);指定された位置にある要素を戻す<br>
**・要素の置換**<br>
　list.set(index,"A");すでに存在する要素を、indexを指定して置き換える。<br>
**・削除**<br>
　list.remove(index);<br>
**・検索**<br>
　list.indexof("A");<br>

    public class ListExercise {
        public static void main(String[] args) {
            List<String> list = new ArrayList<>();
            list.add("apple"); // size=1
            list.add("pear"); // size=2
            list.add(0,"banana");
            list.set(2,"melon");
            list.add("apple"); // 重複のデータも追加できます
            System.out.println(list.size());
            for(String i : list){
            	System.out.println(i);
            }
            int index = list.indexOf("banana");
            list.remove(index);
            System.out.println("要素[0]:" + list.get(0));
            try {
                System.out.println("要素[6]:" + list.get(6));
            } catch (IndexOutOfBoundsException indexOutOfBoundsException ) {
                System.out.println("要素[6]:例外発生");
            }
        }
    }

Listと配列の変換

    String array[] = list.toArray(new String[4]);

Listの種類<br>
**ArrayList　LinkedList**<br>
**・ArrayList長所と短所**<br>
特定の要素にアクセスするスピードが早い<br>
要素を追加するスピードが遅い<br>
**・LinkedList長所と短所**<br>
要素を追加したり削除するスピードが早い<br>
特定の要素にアクセスするスピードが遅い<br>
http://bowtin.hatenablog.com/entry/2018/01/24/145452<br>

**■Map**
Mapはインデックスとなるkeyとそのデータとなるvalueの両方を定義することができます。keyには整数値のほかにString型などの変数なども指定することができます。keyに指定した変数から、valueを呼び出すことができます。
Mapのキーは重複させることはできません。キーと値が１対になった要素を持ちます。
これに対して、Listは要素を格納した順に自動的に整数値のインデックスが生成され、値と紐づけされます。
Listの要素はインデックス番号を指定して、値を呼び出します。keyと関連付けて値を保持する必要がある場合はMapが適しています。
Mapの定義

    HashMap<型1,型2> 変数名 = new HashMap<型1,型2>();

MapのkeyはString型、valueはInteger型で指定されています。型の指定はクラス型で行います。
int型などのプリミティブ型は使用できないので注意しましょう。

**・要素を格納する**<br>
map.put(key,value)<br>
map.put("りんご", "apple");<br>
map.put("ぶどう", "grapes");<br>
**・要素を取り出す。要素を取り出すにはキーを指定し、そのキーに対応した要素を取り出すことになります**<br>
map.get(key)<br>
System.out.println(map.get("りんご"));<br>
**・要素を取得する前に、要素を指定するためのキーがマップに登録されているかどうかを先に確認する事も出来ます。**v
map.contains(key)<br>

    public class MapExercise {
    	public static void main(String args[]){
    	    HashMap<String,String> map = new HashMap<String,String>();
    
    	    map.put("りんご", "apple");
    	    map.put("ぶどう", "grapes");
    
    	    if (map.containsKey("りんご")){
    	      System.out.print("りんごを英語にすると");
    	      System.out.println(map.get("りんご"));
    	    }else{
    	      System.out.println("指定したキーは存在しません");
    	    }
    	  }
    }

**・要素を削除する**<br>
map.remove(key)<br>
map.remove("ぶどう");<br>
すべての要素を削除する<br>
map.clear()<br>



	    if (map.containsKey("ぶどう")){
	      System.out.print("ぶどう英語にすると");
	      System.out.println(map.get("ぶどう"));
	    }else{
	      System.out.println("指定したキーは存在しません");
	    }
	    
	    map.clear();
	    if (map.containsKey("りんご")){
		      System.out.print("りんごを英語にすると");
		      System.out.println(map.get("りんご"));
		    }else{
		      System.out.println("指定したキーは存在しません");
		    }
	    
	  }

ループを回して、すべての要素を取り出す
<> には「ダイヤモンド演算子（オペレータ）」という名前です。初期化して変数に代入するタイミングで、生成するクラスの型を推理してくれるという便利機能。



    public class MapExercise {
        public static void main(String[] args) {
            Map<String, Integer> map = new HashMap<>();
            map.put("apple", 123);
            map.put("pear", 456);
            map.put("banana", 789);
            for (String key : map.keySet()) {
                Integer value = map.get(key);
                System.out.println(key + " = " + value);
            }
        }
    }

entrySet() マップに含まれるキーと値のSetを返す

    public class MapExercise {
        public static void main(String[] args) {
            Map<String, Integer> map = new HashMap<>();
            map.put("apple", 123);
            map.put("pear", 456);
            map.put("banana", 789);
            for (Map.Entry<String, Integer> entry : map.entrySet()) {
                String key = entry.getKey();
                Integer value = entry.getValue();
                System.out.println(key + " = " + value);
            }
        }
    }

毎回プリントされた順番が違うことがあり得ます。

**■Set**
要素の重複は不可です。Mapとの区別は、Keyだけ格納します。
使っているmethodはmapとほどんど同じです。

    public class SetExercise {
    public static void main(String[] args) {
            Set<String> set = new HashSet<>();
            System.out.println(set.add("abc")); // true
            System.out.println(set.add("xyz")); // true
            System.out.println(set.add("xyz")); // false
            System.out.println(set.contains("xyz")); // true，元素存在
            System.out.println(set.contains("XYZ")); // false
            System.out.println(set.remove("hello")); // false
            System.out.println(set.size()); // 2
            for (String s : set) {
                System.out.println(s);
            }
        }
    }


 
