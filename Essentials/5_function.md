# function and function_template

Todo

引入概念

fn fnName(param paramSet pair) retSet:
    $domFact1(param) # x > 0
    $domFact2(param) # y < 0
    then:
        $propertyOfFnName(..)
        $propertyOfFnName(...)

fn f(x, y R) R:
    x > 0
    y < 1
    y % 2 = 0
    then:
        f(x, y ) = 1

fn_template template_of_f(x, y R) R:
    x > 0
    y < 1
    y % 2 = 0
    then:
        f(x, y ) = 1

f $in template_of_f

fn f(x, y R) R:
    dom:
        ...
    then:
        ...

fn_template temp(x,y R) R:
    f(x,y R)

fn_tempalate XXX(x, y R) R:
    dom:
        x > 0
        y < 1
        y % 2 = 0
    then:
        f(x,y) = 1
        f(x,y) $in R

f $in XXX

fn_template seq(params):
    fn (x N) retParam:
        dom:
            ...
        then:
            ...

let a seq(R)
fn a(x N) R

prop is_group(s set, id s, plus fn(s,s)s, reverse fn(s)s)

let f fn(s,s)s

fn f(s,s)s

fn_template matrix(line, column N_pos, s set):
    fn (x, y N) s:
        x < line
        y < column

2 * 2 matrix, with values in R

let m matrix(2,2,R):
    m(0,0)