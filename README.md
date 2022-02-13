# HighLight


להדגיש טקסט:
1.	ליצור מתודת extension כזו:
fun TextView.highlight(highlight: String) {
    val tvt = text.toString()
    var ofe = tvt.indexOf(highlight, 0)
    val wordToSpan: Spannable = SpannableString(text)
    var ofs = 0
    while (ofs < tvt.length && ofe != -1) {
        ofe = tvt.indexOf(highlight, ofs)
        if (ofe == -1) break else {
            // set color here
            wordToSpan.setSpan(
                StyleSpan(Typeface.BOLD),
                ofe,
                ofe + highlight.length,
                Spannable.SPAN_EXCLUSIVE_EXCLUSIVE
            )
            text=(wordToSpan)
        }
        ofs = ofe + 1
    }
2.	להגדיר liveData ב-viewModel:

val highlightText=MutableLiveData<String>("Initial value");

3.	ב-searchView listener להוסיף:

viewModel.highlightText.value=newText

4.	להוסיף ב-bind של ה-viewHolders את הקריאה ל-extension

itemView.name.highlight(highlight)

![image](https://user-images.githubusercontent.com/55790024/153771835-35e2f073-563a-4b00-b65f-0058a41b61e7.png)
