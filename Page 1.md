# Nonogram (making)
- 1:*で塗って-で塗らない箇所を分割する
- 2:以下2行、rowは右上に、colは左下に追加
  - =BYrow(塗った範囲,LAMBDA(t,lambda(ct,if(len(SUBSTITUTE(ct,"-",""))>0,SPLIT(ct,"-",false,true),""))(CONCATENATE(t))))
  - =BYcol(塗った範囲,LAMBDA(t,lambda(ct,if(len(SUBSTITUTE(ct,"-",""))>0,TRANSPOSE(SPLIT(ct,"-",false,true)),""))(CONCATENATE(t))))
- 3:以下2行が数字ヒントを書き出してくれる
  - =BYROW(2のbyrowが書き出した範囲,LAMBDA(t,ifna(LAMBDA(u,if(COUNTIF(u,0)>0,LAMBDA(v,w,HSTACK(v,w))(FILTER(u,u=0),FILTER(u,u<>0)),u))(ARRAYFORMULA(LEN(t))),"0")))
  - =BYCOL(2のbycolが書き出した範囲,LAMBDA(t,IFNA(LAMBDA(u,if(COUNTIF(u,0)>0,LAMBDA(v,w,vSTACK(v,w))(FILTER(u,u=0),FILTER(u,u<>0)),u))(ARRAYFORMULA(LEN(t))),"0")))

# Putteria
- 数字しかない状態であれば上下左右のチェックはこれ (※B3:H3を適時差し替える事)
  - =or(COUNTIF(B$3:B$9,B3)>1,COUNTIF($B3:$H3,B3)>1)
- 数字以外も入れるとなった場合はまず数字かどうかを判定する所から(Venneriaの可能性に警戒しよう)

# 横書きにおけるMakearrayとXY座標の関係
- =MAKEARRAY(幅,高さ,LAMBDA(y,x,関数本体))

# OFFSET型XLOOKUP
- =XLOOKUP(a, offset(b,0,0,h,w), offset(b,r,c,h,w), navl, mmode, smode)
