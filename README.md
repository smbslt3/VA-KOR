# VA-KOR

본 repo에서는 Lee et al. (2022)의 연구 *Emotion Evaluator: Expanding the Affective Lexicon with Neural Network Model* [^1] 에서 사용한 한국어 정서 어휘집 자료에 대해 다룹니다.

## 한국어 정서 어휘집 (Korean Affective Lexicon)

영어 단어의 정서적 의미를 평정한 데이터는 많으나[^2], 이에 대응되는 한국어 정서 어휘집 자료는 매우 적습니다. Lee et al. (2022)의 연구에서는 이러한 제한점을 극복하기 위해 선행 한국어 정서 어휘집 자료를 종합하였습니다.



| **저자***       | **Valence** | **Arousal** | **그 외 측정 차원** | **평가 척도(점수)** | **단어 수** |
|---------------|-------------|-------------|---------------|---------------|----------|
| **민경환(2005)** | 쾌-불쾌        | 활성화         | 원형성, 친숙성      | 1~7           | 434      |
| **고일주(2013)** | Valence     | Activation  | -             | 1~7**         | 267      |
| **이윤형(2016)** | 정서가         | 각성가         | 구체성           | 1~9           | 450      |
| **김청택(2022)** | Valence     | Arousal     | -             | -3~3          | 257      |

\* 저자는 각 연구의 교신저자를 명시  
\** 고일주(2013)의 본문에서는 1~7의 범위로 설문을 수행했다고 보고하였으나, 부록에 공개된 데이터는 Valence: -1\~1, Activation: 0\~2의 값을 띄고 있음.





## 데이터셋

1. `VA_KOR_2005_MIN.csv`  
   - 자료 출처
     - 박인조, & 민경환. (2005). 한국어 감정단어의 목록과 정서 차원 탐색. *한국심리학회지: 사회및성격*, *19*(1), 109-129.  
  
2. `VA_KOR_2013_KO.csv`  
   - 자료 출처
     - 이신영, & 고일주. (2013). 소셜 미디어에서 사용되는 한국어 정서 단어의 정서가, 활성화 차원 측정. *감성과학*, *16*(2), 167-176.
   - 값의 범위는 부록을 따라 Valence: -1\~1, Activation: 0\~2 입니다.
   
3. `VA_KOR_2016_LEE.csv`  
   - 자료 출처
     - 홍영지, 남예은, & 이윤형. (2016). 정서가, 각성가 및 구체성 평정을 통한 한국어 정서단어 목록 개발. *인지과학*, *27*(3), 377-406.  
   - **전기**와 **책장**, 두 개의 동음이의어가 있습니다. **책장**의 경우 다음과 같이 저자의 답변을 받았으나, **전기**의 경우 받지 못했습니다.

      > 단어 빈도 191의 책장(冊欌; bookshelf)은 책을 넣어두는 장의 의미를 있습니다. 반면 단어 빈도 81의 책장(冊張; page)은 책을 이루고 있는 낱낱의 장을 의미합니다.
      
4. `VA_KOR_2022_KIM.csv`  
   - 자료 출처  
     - Lee, J., Lim, J., Park, J., & Kim, C. (2022). Emotion Evaluator: Expanding the Affective Lexicon with Neural Network Model. In *Proceedings of the Annual Meeting of the Cognitive Science Society* (Vol. 44, No. 44).  
   - Lee et al. (2022)의 연구에서는 평가자에게 단어와 함께 뜻풀이를 제공했기 때문에 이 자료에는 단어의 정서가 평정시 제시된 뜻풀이가 포함되어 있습니다.
   - **짜릿하다†**, **격파†** 는 단어의 정서가를 수집하였으나 연구에서 활용되지 않은 단어입니다.
   - **침울하다\***, **만년필\***, **생기\*** 는 단어의 정서가를 수집하였으나 민경환/이윤형의 자료와 중복되어 연구에서 활용되지 않은 단어입니다.

   

5. `VA_KOR_concat.csv`

   - 상기 4개의 자료를 결합한 자료입니다.
   - 각 연구에서 공통적으로 측정한 Valence와 Arousal만 추출하여 -3\~3의 범위로 정규화 했습니다.
   - 단어에 표기된 첨자(`*, †`)를 제거하였습니다.
   - **중복 단어가 처리되지 않았습니다.** 자료 활용시 이 부분에 유의하시기 바랍니다.
   - **이윤형(2016)의 자료에 있는 동음이의어가 처리되지 않았습니다.** 자료 활용시 이 부분에 유의하시기 바랍니다.

   

6. `VA_KOR_annot.csv`

   - Lee et al. (2022)의 연구에서 사용한 자료입니다. 
   - 5.의 자료에서 중복값을 통합하고 일부 단어를 제외하였습니다.
     - **고일주**의 연구에서 31개 단어를 제외하였습니다.
     - **김청택**의 연구에서 5개 단어를 제외하였습니다.
     - 연구 간 중복되는 단어(**민경환\-이윤형: 31개**, **고일주\-이윤형: 1개**)를 통합하였습니다. V, A값은 평균하였으며, 단어의 출처는 `이윤형*` 으로 할당하였습니다.
   - 각 단어에 국어사전의 뜻풀이를 추가하였습니다.
     - 단어의 뜻풀이는 표준국어대사전, 우리말샘, 고려대학교 한국어대사전을 참고하였습니다.
     - 이윤형의 자료에 있는 동음이의어 **책장**을 `책장(책을 꽂아두는 장)`과 `책장(책의 낱장)`으로 단어를 교체하였습니다.
     - 이윤형의 자료에 있는 동음이의어 **전기**의 경우, 동음이의어 문제를 해결할 수 없으나 V, A값의 차이가 크지 않아 뜻풀이를 임의로 할당하였습니다.


![VA_annot](https://github.com/smbslt3/VA-KOR/assets/41793074/20a0a607-5cf7-4239-b45a-6b190617b57d)



## 인용

- 개별 연구 자료(`데이터셋 1,2,3`)만을 사용하는 경우 해당 연구를 인용해주시기 바랍니다.
- Lee et al. (2022)의 자료 또는 통합된 자료(`데이터셋 4,5,6`)를 이용하는 경우 아래 연구를 인용해주시기 바랍니다.
  - APA style
    - Lee, J., Lim, J., Park, J., & Kim, C. (2022). Emotion Evaluator: Expanding the Affective Lexicon with Neural Network Model. In *Proceedings of the Annual Meeting of the Cognitive Science Society* (Vol. 44, No. 44).
  - BibTeX

        @inproceedings{lee2022emotion,
          title={Emotion Evaluator: Expanding the Affective Lexicon with Neural Network Model},
          author={Lee, Junho and Lim, Jaeseo and Park, Jooyong and Kim, Cheongtag},
          booktitle={Proceedings of the Annual Meeting of the Cognitive Science Society},
          volume={44},
          number={44},
          year={2022}
        }




[^1]: https://escholarship.org/uc/item/20s0r7c1
[^2]: https://saifmohammad.com/WebPages/NRC-Emotion-Lexicon.htm 
