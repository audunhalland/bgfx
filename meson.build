project('bgfx', 'cpp', 'c', 'objcpp')
bx = subproject('bx')
include_priv = include_directories('3rdparty', '3rdparty/dxsdk/include', '3rdparty/khronos', 'include')

if host_machine.system() == 'darwin'
  source = 'src/amalgamated.mm'
  deps = dependency('appleframeworks', modules : ['OpenGL'])
else
  source = 'src/amalgamated.cpp'
  deps = []
endif

include = [include_directories('include'), bx.get_variable('include')]
lib = static_library('bgfx', source,
                     include_directories : [include_priv, bx.get_variable('include')],
                     dependencies : deps)

shaderc_sources = [
    'tools/shaderc/shaderc.cpp',
    'tools/shaderc/shaderc_glsl.cpp',
    'tools/shaderc/shaderc_hlsl.cpp',
    '3rdparty/fcpp/cpp1.c',
    '3rdparty/fcpp/cpp2.c',
    '3rdparty/fcpp/cpp3.c',
    '3rdparty/fcpp/cpp4.c',
    '3rdparty/fcpp/cpp5.c',
    '3rdparty/fcpp/cpp6.c',
    '3rdparty/glsl-optimizer/src/glsl/ast_array_index.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ast_expr.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ast_function.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ast_to_hir.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ast_type.cpp',
    '3rdparty/glsl-optimizer/src/glsl/builtin_functions.cpp',
    '3rdparty/glsl-optimizer/src/glsl/builtin_types.cpp',
    '3rdparty/glsl-optimizer/src/glsl/builtin_variables.cpp',
    '3rdparty/glsl-optimizer/src/glsl/glcpp/glcpp-lex.c',
    '3rdparty/glsl-optimizer/src/glsl/glcpp/glcpp-parse.c',
    '3rdparty/glsl-optimizer/src/glsl/glcpp/pp.c',
    '3rdparty/glsl-optimizer/src/glsl/glsl_lexer.cpp',
    '3rdparty/glsl-optimizer/src/glsl/glsl_optimizer.cpp',
    '3rdparty/glsl-optimizer/src/glsl/glsl_parser.cpp',
    '3rdparty/glsl-optimizer/src/glsl/glsl_parser_extras.cpp',
    '3rdparty/glsl-optimizer/src/glsl/glsl_symbol_table.cpp',
    '3rdparty/glsl-optimizer/src/glsl/glsl_types.cpp',
    '3rdparty/glsl-optimizer/src/glsl/hir_field_selection.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_basic_block.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_builder.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_clone.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_constant_expression.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_equals.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_expression_flattening.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_function.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_function_can_inline.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_function_detect_recursion.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_hierarchical_visitor.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_hv_accept.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_import_prototypes.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_print_glsl_visitor.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_print_metal_visitor.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_print_visitor.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_rvalue_visitor.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_stats.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_unused_structs.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_validate.cpp',
    '3rdparty/glsl-optimizer/src/glsl/ir_variable_refcount.cpp',
    '3rdparty/glsl-optimizer/src/glsl/link_atomics.cpp',
    '3rdparty/glsl-optimizer/src/glsl/link_functions.cpp',
    '3rdparty/glsl-optimizer/src/glsl/link_interface_blocks.cpp',
    '3rdparty/glsl-optimizer/src/glsl/link_uniform_block_active_visitor.cpp',
    '3rdparty/glsl-optimizer/src/glsl/link_uniform_blocks.cpp',
    '3rdparty/glsl-optimizer/src/glsl/link_uniform_initializers.cpp',
    '3rdparty/glsl-optimizer/src/glsl/link_uniforms.cpp',
    '3rdparty/glsl-optimizer/src/glsl/link_varyings.cpp',
    '3rdparty/glsl-optimizer/src/glsl/linker.cpp',
    '3rdparty/glsl-optimizer/src/glsl/loop_analysis.cpp',
    '3rdparty/glsl-optimizer/src/glsl/loop_controls.cpp',
    '3rdparty/glsl-optimizer/src/glsl/loop_unroll.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_clip_distance.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_discard.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_discard_flow.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_if_to_cond_assign.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_instructions.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_jumps.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_mat_op_to_vec.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_named_interface_blocks.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_noise.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_offset_array.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_output_reads.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_packed_varyings.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_packing_builtins.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_ubo_reference.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_variable_index_to_cond_assign.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_vec_index_to_cond_assign.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_vec_index_to_swizzle.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_vector.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_vector_insert.cpp',
    '3rdparty/glsl-optimizer/src/glsl/lower_vertex_id.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_algebraic.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_array_splitting.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_constant_folding.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_constant_propagation.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_constant_variable.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_copy_propagation.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_copy_propagation_elements.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_cse.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_dead_builtin_variables.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_dead_builtin_varyings.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_dead_code.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_dead_code_local.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_dead_functions.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_flatten_nested_if_blocks.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_flip_matrices.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_function_inlining.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_if_simplification.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_minmax.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_noop_swizzle.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_rebalance_tree.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_redundant_jumps.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_structure_splitting.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_swizzle_swizzle.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_tree_grafting.cpp',
    '3rdparty/glsl-optimizer/src/glsl/opt_vectorize.cpp',
    '3rdparty/glsl-optimizer/src/glsl/s_expression.cpp',
    '3rdparty/glsl-optimizer/src/glsl/standalone_scaffolding.cpp',
    '3rdparty/glsl-optimizer/src/glsl/strtod.c',
    '3rdparty/glsl-optimizer/src/mesa/main/imports.c',
    '3rdparty/glsl-optimizer/src/mesa/program/prog_hash_table.c',
    '3rdparty/glsl-optimizer/src/mesa/program/symbol_table.c',
    '3rdparty/glsl-optimizer/src/util/hash_table.c',
    '3rdparty/glsl-optimizer/src/util/ralloc.c'
]

shaderc_includes = [
    include_priv,
    bx.get_variable('include'),
    include_directories('3rdparty/fcpp'),
    include_directories('3rdparty/glsl-optimizer/include',
                        '3rdparty/glsl-optimizer/src',
                        '3rdparty/glsl-optimizer/src/glsl',
                        '3rdparty/glsl-optimizer/src/mesa')
]

if host_machine.system() != 'windows'
    # Very noisy build, turn off all warnings
    shaderc_c_args = ['-w']
    shaderc_cpp_args = ['-w']
else
    shaderc_c_args = []
    shaderc_cpp_args = []
endif

shaderc = executable('shaderc', shaderc_sources,
                     include_directories : shaderc_includes,
                     c_args : shaderc_c_args,
                     cpp_args : shaderc_cpp_args)
