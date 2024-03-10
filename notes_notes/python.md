# python 

## numpy
### np_array_name =  np.array(array_name) for converting a normal array into np array \
### normal python list takes up a lot of space even if the list is empty all bcz of the meta data and stuff
### np.arange(\[start\], stop, \[step\], \[dtype=None\]) it returns an nd.array unlike range
### linspace(start, stop, num=nums_of_elements, endpoint=True, retstep=False)
### np.ndim()
### np.dtype()
### np.shape() // returns a tuple
### indexing and slicing works just like python
### slicing an array just creates view and not a copy
### a\[start:stop:range\]
### np_array.reshape() no less no more just right 
### np.may_share_memory(a, b)
### np.ones(tuple_shape, dtype)
### np.zeros(tuple_shape, dtype)
### np.ones_like(another_array)
### np.zeros_like(another_array)
### np.empty(size) //garbage values
### // testing what type of flags it it
### x.flags('C_F_CONTIGUOUS | F_CONTIGUOUS | C_CONTIGUOUS | F_CONTIGUOUS | OWNDATA | WRITEABLE | ALIGNED | UPDATEIFCOPY')
### y = x.copy(order="K | C | F")
### np.identity(n, dtype=Type) //dim nxn
### eye(n, m, k=0, dtype=Type) //not for square arrays //and k for which col the 1 will start
### type()
### using scalars on numpy arrays array + constant
### subtraction, multiplication, division, and addition on numpy arrays
### adding two matrices a+b
### multiplication of two arrays a\*b its so easy
### for doing the dot product we do the np.dot(a, b)
### .transpose()
### multiplication using broadcasting a\*b\[;, np.newaxis()\]
### np.abs()
### a.reshape(new, dimensions)
### dtype can be an array of tuples of (name, type) and you can get that whole column using the colname in python
### like the dt = np.dtype(\[('colname', 'type')\]) and that defines an array
### you can access the whole col using the array_name\['colname'\]
### you can have multiple cols like that in one array just have array of multiple typles in the type array
### print(population_table\['area'\]\[2:5\]) // gives the 2-4 row elements in area col
### < little endian  |
### > big endian     |  // this is the byte order
### = native         | linux default is little endian
### dt.name // name of the type
### dt.byteorder
### dt.size //no of bytes 
### if lowercase b then binary strings so instead of s20 or something do np.unicode, 20 as the type
### for any arithmetic operation with a scalar on a numpy array just do it as it was a variable
### np.random.randint(start, stop, size)
### a\*b multiplication of two matrices is component wise if you are just creating arrays and doing * if youre doing np.dot() its matrix multi or else if you do np.mat() to convert it into matrix then it will work with * also
### np.array_equal(a, b)
### if you do a == b youll get a boolean array for comparing there is np.array_equal()
### np.logical_or(a, b) or np.logical_and(a, b) does component wise comparison 
### B = np.array(\[\[1, 2, 3\],\] * 3) creates a 2d array of you know what
### B\[:, np.newaxis\] makes every element individually an array of dim 1 adds dimensions inside the array
### B\[np.newaxis, :\] is the same as np.array(\[\[1, 2, 3\],\] * 3).transpose() adds dimention outside
### np.concatinate() adds just adds the arrays int to bigger size array and opens the innermost dimention up
### np.concatinate() for 3d only default one is rowwise concatination and read rowwise too
### np.concatinate(axis=1) do put them next to each other and read them rowwise
### np.tile(a, (x, y)) //what to tile and the dimension
### print(np.abs(dists - dists\[:, np.newaxis\])) distance matrix
### np.flatten() // flatten to one dimension
### np.flatten(a, order="C") // into a single dimention for 3d do the height wise first then move row wise
### np.flatten(a, order="F") // into a single dimention for 3d do the base first columnwise and then do the next floor
### np.ravel() // same thing but mutates the same array 
### np.row_stack() stack them one below the other and read in rowwise its almost like concatinate but don't remove the inner brackets tha't it
### np.column_stack() first make the array a column and then put them beside each other if it's a 3d array make sure you imagine the 1d array standing
### np.dstack() just do the z axis stacking and read them rowwise
### a.astype(some_valid_type) // to convert to that type
### A = np.array(\[3,4,6,10,24,89,45,43,46,99,100\])
### div3 = A\[A%3!=0\] // to find all the numbers that are divisible by 3
### np.nonzero(a) //returns array of x co and y co whose combination produces coordinates in which the element value is nonzero
### np.flatnonzero()
### np.count_nonzero()
  
## matplotlib

### plt.plot(\[-1, -4.5, 16, 23\], "ob") just plot implicit x axis from 0 and ob is o marker blue color
### fig, ax = plt.subplots(), xlabel="", ylabel="", title="" you can even do 2, 2, figsize=(,) and to ax\[0, 0\].plot() in order to do subplots
### ax.plot() and inside that all the x, y axis pairs ,color ,marker ,linestyle ,linewidth ,label
### ax.bar() x y and color=""
### ax.hist() y values and bins= // bins is no of bars you want to plot
### ax.scatter() x, y, color, marker s=int for size
### ax.stackplot(x, y1, y2, y3)
### ax.pie(value, label=label_array, explode=explode_array, autopct="%some_format%", shadow=boolean, startangle=int)
### and also for pie ax.axis("equal") means that pie is drawm as a circle
### np.pi is used to do caldulations with pi values
### ax.set_xticks(array)
### ax.get_xticks()
### ax.get_xticklables()
### ax.set_yticks(array)
### ax.get_yticks()
### ax.get_yticklables()
### ax.xaxis.set_ticks_position('bottom')
### ax.spines\['bottom'\].set_position(('data',0))
### ax.yaxis.set_ticks_position('left')
### ax.spines\['left'\].set_position(('data',0))
  
## pandas

### pd.Series()
### you can do S.index and S.values // which are of type numpy ndarray
### you can set index=index_array for any series to make it the index
### if you concatinate 2 Series the if an index exists in both then added else NaN
### to access a row Series_name\['row_name'\] accessing multi indexes is Series_name \\[\\['index1', 'index2', 'index3'\]\]
### S.apply(lambda x: x if x > 50 else x+10 ) you can do this and do any function you want
### if pd.Series(some_dict) then key is index and value is values
### due to NaN values the other values can be turned into float
### isnull() given true if NaN else false
### notnull() does the oppsite
### None in dict is NaN in Series
### pd.dropna will return a series of only not null data
### to fill something instead of just deleting the NaN rows yo do pd.fillna(0 | something) // you can call fillna with a dict to fill appropriate data
### you can do astype(int) to convert values to int just like in nparrays
### you can give names to the columns with Series_name.columns = columns_array
### you can make dataframes from dicts which have values as arrays
### pd.DataFrame(the_dictionary, columns=col_array) // will rearrange them in terms of the ordering in col_array
### we can reorder the rows using DF.reindex(index=new_index_arr)
### to rename the cols after creation you supply a dict with old names as key and new names as value
### DF.rename(column=new_dict) // dict of old names and new names inplace=True to mutate inplace instead of returning a mutated copy
### DF.set_index("col_name") // to set a col as index can do inplace=True 
### print(city_frame.loc\["Germany"\]) // select all rows with index Germany
### print(city_frame.loc\[\["Germany"\],\["france"\]\]) // select all rows with index Germany and France remember array of arrays
### print(city_frame.loc\[condition\]) // select all rows which satisfies a condition
### print(city_frame.loc[condition1 & condition2]) you can give more than one condition with this
### city_frame.loc['Switzerland'] = ['Zurich', 415215] // can add a new row list lika a new pair in the dict
### city_frame.insert(loc=idx, column='area', value=area) // inserting cols into DFs
### df = pd.DataFrame(columns=['lib', 'qty1', 'qty2']) // creating empty df
### you can do DF.T to transpose that mf
### if you want to access by using row and col do DF.loc([row_name. col_name]) // remember 1 [] bracket when you are accessing multiple rows then [[]] brackets
