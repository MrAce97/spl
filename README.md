~~~ LISP
# spl
;9 Определите функцию, разделяющую исходны список на два подсписка. Первый из них должны попасть элементы с нечетными номерами, во второй элементы с четными номерами.

(defun sort-lst(lst)
(cond
	((null (cdr lst)) (list lst))
	(t 
		((lambda (lst1)
		(list
			(cons (car lst) (car lst1))
			(cons (cadr lst) (cadr lst1))))
		(sort-lst (cddr lst)))
	)
)
)




; 40
; Определите функцию разностт формирующую разность двух множеств, т.е. удал€ющую 
; из первого множества все общие со вторым множеством элементы
(defun разность (lst1 lst2)
	((lambda (head body difference)(
		cond
			((null lst1) nil)
			((member_ head lst2) difference))
			(T (cons head difference))
		))(car lst1) (cdr lst1) (разность body lst2))

)
(defun member_ (el lst)
   (
	cond 
		((null lst) nil)
		((equal (car lst) el) T)
		(T (member el (cdr lst)))
	
    )

)

;Функции высших порядков
;2.Определите функционал (MAPLIST fn список) для одного списочного аргумента

(defun maplist_(fn lst)
    (cond ((null lst) nil)
          (t (cons (funcall fn (car lst)) (maplst fn (cdr lst))))
         )                 
    )
    


;4.Определите функциональный предикат (каждый пред cписок), который истинен только в том случае, когда €вл€ющийс€ функц аргументом
;предикат истинен дл€ всех элементов списка список.

(defun response(el) 
                        (if (> el 4) nil (list t))
                     
                     )

(defun каждый(lst) 
                   (null (mapcan #'response lst))
                    )

(print (каждый '(5 6 8)))

;6.Определите фильтер (удал пред список), удал€ющий из списка все элементы, которые обладают свойством наличие которого ;определ€ет предикат пред

(defun response(el) 
                        (if (> el 4) nil (list el))
                     
                     )

(defun удалить(lst) 
                  (mapcan #'response lst)
                    )

(print (удалить '(1 2 8)))

;8. Напишите генератор натуральных чисел: 0, 1, 2, 3, 4, 5, ... 
 (defun generator () 
                     
                         (let ((x 0)) 
                                 (lambda () (setq x (+ x 1))))
   )
(setq s1 (generator))


(write (funcall (generator)))


;Макросы

;1. Определите макрос, который возвращает свой вызов. 


(defmacro func (&rest x)
 `(quote (func ,x)))
 (func 1 2 3)
 
 ;2. Определите макрос (POP стек), который читает из стека верхний элемент и меняет значение переменной стека. 
 (defmacro somepop (stack)
  `(let ((first (car ,stack)))(setq ,stack (cdr ,stack))first))
  
 ;3. Определите лисповскую форму (IF условие p q) в виде макроса. 
 (defmacro myif (res p q)
    `(if res,p,q))
  (write (myif (> 3 2 )3 2) )
~~~
HASKELL
~~~ haskell
; Заменяет все вхождения элемента
rep :: [Integer] -> Integer -> Integer -> [Integer]
rep [] _ _ = []
rep (x:xs) element value = if element == x then value:rep xs element value else x:rep xs element value


;;нечетные
odd :: [Integer] -> [Integer]
odd (x:[]) = x: []
odd (x:xs) = x : odd (tail xs)

;;произведение векторов
multivec :: [Integer] -> [Integer] -> Integer
multivec [] []= 0
multivec (x:xs) (y:ys) = (y*x) + (multivec xs ys)
~~~
