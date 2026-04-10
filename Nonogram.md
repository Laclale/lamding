1:*で塗って-で塗らない箇所を分割する
2:以下2行、rowは右上に、colは左下に追加
=BYrow(塗った範囲,LAMBDA(t,SPLIT(CONCATENATE(t),"-",false,true)))
=BYcol(塗った範囲,LAMBDA(t,TRANSPOSE(SPLIT(CONCATENATE(t),"-",false,true))))
3:以下2行が数字ヒントを書き出してくれる
=BYROW(2のbyrowが書き出した範囲,LAMBDA(t,LAMBDA(u,if(COUNTIF(u,0)>0,LAMBDA(v,w,HSTACK(v,w))(FILTER(u,u=0),FILTER(u,u<>0)),u))(ARRAYFORMULA(LEN(t)))))											
=BYCOL(2のbycolが書き出した範囲,LAMBDA(t,LAMBDA(u,if(COUNTIF(u,0)>0,LAMBDA(v,w,vSTACK(v,w))(FILTER(u,u=0),FILTER(u,u<>0)),u))(ARRAYFORMULA(LEN(t)))))									
									
									
									
									
									
									
									
									
									
									
									
									
