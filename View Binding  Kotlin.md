
## View Binding について
- View Bindingを使用することによって、[ FindViewById ]を使わずにUI画面のView（部品）に直接アクセスすることが可能
- Android Studio 3.6以降で使うことができ、インストールは不要（既にインストール済み）

## View Binding を使う準備
- View Binding は自動でXMLレイアウトファイルがあれば、ファイル内に ** tools:viewBindingIgnore="true" ** と記述する
- 自動生成されるクラス（バインディングクラス）の名前は、XMLファイル名（snake_case）をPastalCase(UpperCamelCase)に変換してからBindingにくっつけたものになる
　- ex: ** activity_main.xmlファイル **からは ** ActivityMainBinding ** クラスが生成される
 - 生成されたクラス（バインディングクラス）には下記のフィールドやメソッドがある
 　- レイアウト内の、View部品(レイアウト時に　** id ** をつけなかったものは含まれない)
   - root ・・・ ルートビュー（UI部品の土台になっているレイアウトview）への参照
   - getRoot()メソッド ・・・ ルートビュー（root）を参照
   - inflate()メソッド ・・・ バインディングクラスのインスタンスを生成する
  
  
## Activity での ViewBinding の使いかた
- activity_main.xmlファイルから自動生成されたActivityMainBindingクラスを使用
- MainActivity.ktの中でView(UI部品)を操作するには on Create() メソッドを記述する

```kotlin:MainActivity.kt
private lateinit var binding: ActivityMainBinding

override fun onCreate(savedInstanceState: Bundle) {
    super.onCreate(savedInstanceState)
    binding = ActivityMainBinding.inflate(layoutInflater)
    val view = binding.root
    setContentView(view)
}
```

1. インスタンスを生成 ・・・ バインディングクラスからinflate()メソッドを使ってインスタンスを生成
2. ルードビューへの参照を所得 ・・・ バインディングクラスのルートビュー（root）への参照を所得(rootプロパティ、またはgetRoot()メソッドを使う)
3. 画面のアクティブビュー（表示されるビュー）に設定 ・・・ ルートビューへの参照を ** setContentView() ** に渡す

上記の準備ができれいれば、UIに追加したTextView(idはname)やButton（idはbutton）には次のようにアクセスできる


```kotlin:MainActivity.kt
binding.name.text = "文字列"
binding.button.setOnClickListener { タップされたときの処理 }
```

## FragmentでのViewBindingの使い方
- Fragment ・・・ Avtivityの上で動くActivityより高機能なActivityみたいなもの。タブのように複数画面をひとつにまとめたようなものを扱う際に使う
- Fragmentで使うときはこんなこんな風に設定（メモリリークが起きないように）<br>
※ メモリリークとは・・・ メモリの空き領域が減っていく・確保したメモリ領域の開放忘れが原因（プログラムさんが「ここは僕が使うよ！」と場所取りしたメモリの場所を「もう使わないから他の人が使っていいよ！」にするのを忘れちゃったのが原因で、他の人が使えない状態が続くことによって、メモリの使える場所が減っていくこと。をさす
- 下記の準備ができると、UIに追加したTextView（idはname)やButton(idはbutton)にはActivityの時と同じようにアクセスできる
   
   
```kotlin:HomeFragment.kt
private var _binding: ResultProfileBinding? = null
private val binding get() = _binding!!

override fun onCreateView(
        inflater: LayoutInflater,
        container: ViewGroup?,
        savedInstanceState: Bundle?
): View? {
        _binding = ResultProfileBinding.inflate(inflater, container, false)
        val view = binding.root
        return view
}

override fun onDestroyView() {
        super.onDestroyView()
        _binding = null
}

```


```kotlin:HomeFragment.kt
binding.name.text = "文字列"
binding.button.setOnClickListener { タップされたときの処理 }
```















