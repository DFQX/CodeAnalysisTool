import os

def is_file(filepath):
    return os.path.isfile(filepath)

def is_target_file(filepath, suffixs):
    is_target = False
    for suffix in suffixs:
        if filepath.endswith(suffix):
            is_target = True
            break
    return is_target


def read_filepath(filepath, suffixs):
    '''
    读取指定目录下的所有文件
    '''
    if(is_file(filepath)):
        if is_target_file(filepath, suffixs):
            return [filepath]
        return []
    all_file = []
    file_path = os.listdir(filepath)
    for i in file_path:
        if os.path.isdir(filepath + '\\' + i):
            file_list = read_filepath(filepath + '\\' + i, suffixs)
            if(len(file_list) > 0):
                all_file.extend(file_list)
        else:
            if is_target_file(i, suffixs):
                # print(filepath + '\\' + i)
                all_file.append(filepath + '\\' + i)
    return all_file

def analysis(filelist):
    total_line = 0
    for filepath in filelist:
        with open(filepath, 'r', encoding='utf-8') as f:
            readlines = f.readlines()
            line_count = 0
            for line in readlines:
                if line.strip() != '':
                    line_count += 1
            total_line += line_count
            print(filepath + ': ' + str(line_count))
    print('total line: ' + str(total_line))



if __name__ == '__main__':
    suffixs = ['.dart', '.html']  # 读取指定后缀的文件
    all_file = read_filepath(r'D:\E\project\project\chat\flutter_chat\lib', suffixs)
    analysis(all_file)
