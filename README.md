~~~ LISP
# spl
;9 Определите функцию, раздел€ющую исходны список на два подсписка. ¬ первый из них должны попасть элементы с нечетными номерами, ;во второй элементы с четными номерами.

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
	((lambda (head body)(
		cond
			((null lst1) nil)
			((member_ head lst2) (разность body lst2))
			(T (cons head (разность body lst2)))
		))(car lst1) (cdr lst1) )

)
(defun member_ (el lst)
   (
	cond 
		((null lst) nil)
		((equal (car lst) el) T)
		(T (member el (cdr lst)))
	
    )

)

;функции высших пор€дков
;2.Определите функционал (MAPLIST fn список) для одного списочного аргумента

(defun SORT_(el)

   (cond 
          ((> el 2) (write 99))
          (T nil)
     )
)

(defun MAPLIST_ (fn lst)
         
         (cond 
             ((null lst) nil)
             ((funcall fn (car lst)) (cons (car lst) (MAPLIST_ fn (cdr lst))))
             (T (MAPLIST_ fn (cdr lst)) )
             
          )                 
)

(write (MAPLIST_ #'SORT_ '(1 2 3 4 5 6)))

;4.Определите функциональный предикат (каждый пред cписок), который истинен только в том случае, когда €вл€ющийс€ функц аргументом
;предикат истинен дл€ всех элементов списка список.

(defun SORT_(el)

   (cond 
          ((> el 2) T)
          (T nil)
     )
)

(defun каждый (fn lst)
         
         (cond 
             ((null lst) T)
             ((funcall fn (car lst)) (каждый fn (cdr lst)))
             (T nil)
             
          )                 
)

(write (каждый #'SORT_ '(1 3 4 5 6)))

;6.Определите фильтер (удал пред список), удал€ющий из списка все элементы, которые обладают свойством наличие которого ;определ€ет предикат пред

(defun SORT_(el)

   (cond 
          ((> el 5) T)
          (T nil)
     )
)

(defun удал (fn lst)
         
         (cond 
             ((null lst) nil)
             ((funcall fn (car lst)) (удал fn (cdr lst)))
             (T (cons (car lst) (удал fn (cdr lst) )))
             
          )                 
)

(write (удал #'SORT_ '(1 3 4 5 6)))

~~~
